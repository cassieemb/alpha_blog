# Alpha Blog Project

## Section 1 - Tables and Migrations 

Details
Model name: article

Class name: Article -> Capitalized A and singular, CamelCase

File name: article.rb -> singular and all lowercase, snake_case

Table name: articles -> plural of model name and all lowercase

Additional example:

Model name: user

Class name: User -> Capitalized U and singular, CamelCase

File name: user.rb -> singular and all lowercase, snake_case

Table name: users -> plural of model name

Generate a migration to create a table (in this example articles):

rails generate migration create_articles

To add attributes for the table in the migration file, add the following inside create_table block:

t.string :title

To run the migration file, run the following command from the terminal:

rails db:migrate

The first time you run the migration file, it will create the database, the articles table and a schema.rb file.

To rollback or undo the changes made by the last migration file that was run, you may use the following command:

rails db:rollback

If you have run the rollback step, then you can update the previous migration file and add the following line to add a description attribute (column) to the articles table:

t.text :description
To run the newly edited migration file again, you can run rails db:migrate

Note: This above line will only work if you had rolled back the prior migration.

To generate a new migration file to add or make changes to your articles table you can generate a new file:

rails generate migration name_of_migration_file

Then within the def change method in the migration file you can add the following lines:

add_column :articles, :created_at, :datetime
add_column :articles, :updated_at, :datetime
You can run the newly created migrations file by running rails db:migrate from the command line and check out the schema.rb file to check that the changes were reflected properly.

## Section 3 - Models and Rails Console
To create an article model, create an article.rb model file under app/models folder and fill it in:

class Article < ApplicationRecord

end

Note: Make sure ApplicationRecord is CamelCase.

Now, provided you have the articles table already, you can use the Rails console and work with the articles table using this article.rb model file.

To start the rails console, type in rails console  or rails c from the terminal.

Once in the console, you can exit it at any time by typing in exit followed by enter/return.

You can test out your connection to the articles table by typing the following command from within your rails console:

Article.all

If you get an empty collection/array-like structure as a response, you're good to go.

To create a new article, you can use any of the following methods:

Article.create(title: "first article", description: "Description of first article") # make sure Article is capitalized if using this method
article = Article.new
article.title = "second article"
article.description = "description of second article"
article.save
article = Article.new(title: "third article", description: "description of third article")
article.save
To check all the articles that exist in your articles table, you can use the following command:

Article.all