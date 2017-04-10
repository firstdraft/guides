# Loading data from a CSV file into your database

## 1. Setup

First, Create a folder inside of `lib` called `csvs`

Put your CSV file `example.csv` into the `lib/csvs` folder. In the example below, the file is called `real_estate_transactions.csv`

Make sure you've created a resource with the appropriate columns to match your seed data. The names don't have to match up.

## 2. Read in a CSV file

Let's suppose we ultimately want to run a command named `rails slurp:transactions` which will slurp the data from `real_estate_transactions.csv` and put it in our database.

First, let's create a custom rake task with this name:

```bash
rails generate task slurp transactions
```

This will create a file called `lib/tasks/slurp.rake` that looks like this:

```ruby
namespace :slurp do
  desc "TODO"
  task transactions: :environment do
  end

end
```

Add the following lines between `task transactions: :environment do` and the first `end`:

```ruby
require "csv"

csv_text = File.read(Rails.root.join("lib", "csvs", "real_estate_transactions.csv"))
puts csv_text
```

The first line requires the Ruby CSV library we need to properly parse the CSV data. The next line reads in the CSV file into a variable. The last line prints the contents of the variable. When you run `rake db:seed` you should see a wall of text representing your CSV data. It's a first step, but we've still got a lot of work to do.

We'll keep building off this code until we've created a working seeds file. You should be able to run `rake db:seed` at the end of each step

## 3. Parse the CSV

```ruby
require "csv"

csv_text = File.read(Rails.root.join("lib", "seeds", "real_estate_transactions.csv"))
csv = CSV.parse(csv_text, :headers => true, :encoding => "ISO-8859-1")
puts csv
```

The new line converts the CSV file into a structure that Ruby can read. The `:headers => true` option tells the parser to ignore the first line of the CSV file.

## 4. Looping through the parsed data

```ruby
require "csv"

csv_text = File.read(Rails.root.join("lib", "seeds", "real_estate_transactions.csv"))
csv = CSV.parse(csv_text, :headers => true, :encoding => "ISO-8859-1")
csv.each do |row|
  puts row.to_hash
end
```

This new addition loops through the entire CSV file and converts each row of the document into a hash. The headers of the CSV file will be used as keys for the hash because we added the `:headers => true` option in our previous step.

## 5. Create a database object from each row

```ruby
require "csv"

csv_text = File.read(Rails.root.join("lib", "seeds", "real_estate_transactions.csv"))
csv = CSV.parse(csv_text, :headers => true, :encoding => "ISO-8859-1")
csv.each do |row|
  t = Transaction.new
  t.street = row["street"]
  t.city = row["city"]
  t.zip = row["zip"]
  t.zip = row["zip"]
  t.state = row["state"]
  t.beds = row["beds"]
  t.sq_feet = row["sq_feet"]
  t.category = row["type"]
  t.sale_date = row["sale_date"]
  t.price = row["price"]
  t.lat = row["latitude"]
  t.lng = row["longitude"]
  t.save
  puts "#{t.street}, #{t.city} saved"
end

puts "There are now #{Transaction.count} rows in the transactions table"
```
