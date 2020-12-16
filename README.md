# DevOps Scraper Project

## Steps to make the app run in local machine
- Copy the files over to a Pycharm project, or git clone in your Pycharm Projects directory
- Check the python files individually and install any dependencies that Pycharm notifies you of
- In the Pycharm terminal, run `pip3 install -U pluggy`
### Fixing the broken parts of the app
- In the `test_html_object_manager.py` file it is trying to import a non-existent class but we can see what file
 (`http_manager.py`) it's trying to import from and change the class name to the class in that file
- There is no `HtmlObjectManager` class but there is a `HttpManager` which must be what it meant, so we'll change
 that import line to import `HttpManager` instead
- In the `top_30_csv_generator.py` file, the `generate_top_30_csv` function will need to be edited
- This is because it is currently outputting a new line after every row which will take up more space than necessary
 in our csv and make the csv_generator tests fail as they check for a specific number of lines
 fail
- The line for opening the file should include `newline=''` to fix this, as in the example line below
```python
 with open(csv_file_location + file_name, 'w+', newline='') as top30csv:
```
- All tests should now pass (other than one specific test in the `html_object_manager.py` but we expect this to fail
 locally so this is fine!)