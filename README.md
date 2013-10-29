phase-3 Week 1 Tuesday
=======
* Folders within spec file need to be the same folder structure. Based on the names of the folder, rspec will do different things.
* Any of the spec files need to be _spec. It's how rspec knows to run it.
* 

group test:


### Database Cleaner
Remember test vs development dbs are different. Remember to run `rake db:test:prepare`. 


After ever run, we eed to clean the test db. This is done by in `spec_helper.rb`: 
`config.transactional_fixtures = true`. Test are done as a database transaction. and then it rolls the entire transaction back. 

```ruby
#spec/spec_helper.rb
Rspec.configure do |config|
  config.inclue Capybbara:DSL
  config.mock_with :rspec
  config.transactional_fixtures = true
  config.before (:each, :js => true) do
    Datbase.Cleaner.strategy = :truncation
  end
```
