# Alivia Library system

email: rinmizuki123@gmail.com

## Install Dependencies
`pip install Django==3.0`


## Simple Instructions
Open CMD, go to the floder "libsys"

### Run Server
`python manage.py runserver`
Then you will see 
>Starting development server at http://127.0.0.1:8000/ 
That means run successfully.
Then open http://127.0.0.1:8000/library/ in browser to check.

### As User
- IF YOU ARE NEW USER, plz click the text **'Don't have account?'** to sign up. Remember no 'blank' allowed to use in account name and password. If the account name have been registered, the system will send you a message. The default borrow rule you obey is the one whose id=1.
- IF YOU ARE ALREADY AN USER, plz enter the account name and password to loign. If you enter the account name and password right, you will go to your home page, and enable to go to your personal centre.
- IN PERSONAL CENTER, you can check your personal details and search for books.
    - I want to find Books: You can find books by choosing options,'isbn','title' and 'author'. IF you didn't choose anything, the default option is searching in TITLE.
    - You can check your personal infomations and borrowed History in this page and log out.
- In SEARCHING RESULTS: You can see each searching result's informations. Click the details to see more.
- Details Page: You can check each book's imprint, location and loan status. IF the loan status is **'Available'**, it will display a button which allow you borrow.
- BORROW: The condition of borrowing successfully is that your account status is **'Normal'** and the number of books you keeping is less than your quota. Borrow successful or not, the system will give you a message.

### Create SuperUsers
`python manage.py createsuperuser`
Follow the instructions, enter your account name, email and password(twice).
After create successfully, open http://127.0.0.1:8000/admin in browser. Enter your account name and password to log in.

### Modules and Functions in Backend management
- Accounts
    - The search bar is for searching account name. 
    - There are three actions for superuser operates the selected account.
        - Delete selected accounts
        - use permission: Let the selected account's status change to 'Normal'.
        - freeze account: Let the selected account's status change to 'Freeze'.
        - Just click 'Go' button, the selected records will update. 
    - You also can do single operation, click the drop-down box of account status and choice, but you must always remember to click the 'save' button after the operation.
    - You can click the account id to see the details of account and the book he keeping now. You also can modify some infos which are allowed. But you must always remember to click 'save' botton after modify.
    - Filter is an convenience function to let you filter the accounts quickly.
- Books
    - Search Bar: Find the book quickly by searching ISBN, TITLE, AUTHOR and PUBILSHER.
    - You can click the isbn to check the details of books and the book instances. You can add the books and the infos of each copy of book.
    *The Format of Location: 'blocksname'.'shelf_num'.'book_location'.'copy_num'*
    - Filter is an convenience function to let you filter the books quickly.
- Borrow Rules
    - For each accouts it must obey
- Borrow
    - This part is for borrow records.
    - Search Bar: Find the borrow records qucikly by searching id.
    - You can change the borrow status by click the drop-box. But you must always remember to click 'save' botton after modify.
    - While the borrow status change from 'keeping' to 'returned', the loan status of BOOKINSTANCE won't change from 'on loan' to 'available' directly. The superuser must modify the loan status by himself after put the book back to the bookshelf.
    - Filter is an convenience function to let you filter the borrow records quickly.
- ADD
    - You can add any new infos by usin 'ADD' button in the above of each modules' page or the home page.
- History
    - You can check the modify history in the detail page of each fields.


## Sth Still Confused and Don't have Perfect Solution
- I can't get the values of the time the superuser change the borrow status from 'keeping' to 'returned'. So I can't let the `total_fine()` method stop increasing the value of fine after return book. The superuser only can check the fine and enter the final fine by himself while reader return the book.
- In admin page,  superuser only can search borrow record by borrow ID. I try to let it have a feature to search by account but didn't achieve.
- In default, users will obey the borrow rules with id=1 when they sign up. But what if the superuser delete the records of borrow rules in accident? After delete the record, if we create a new one, the id of it will not be 1.
- And more...


## The End
It's first time I use Django to write a whole web application. There are still many shortcomings, if u have any suggestions, plz contact me by email: rinmizuki123@gmail.com. I will very appreciate if u give me some advice.

