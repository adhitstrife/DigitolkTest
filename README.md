Thought about the code
1. BookingController
    the BookingCOntroller seems functional and working fine but in my opinion there is some aspects that can be improved to achieve a better maintainability, and readability of the code.
    a. What i like about the code
        1. Separation of Conterns
            the code is already using principele of separation of concerns when created where diffrent methods is handling diffrent functions wich meakse the code more modular and easy to understand.
        2. Depedency Injection
            By using BookingRepository it is using a good practice making it easier to replace and mock dependendcies
        3. Comments
            Using comments making it more helpful for understanding the code
    b. Area that i think can be improved
        1. Conditional complexity
            the if-else in index method of the controller can be simplified. you can considering to extracting the conditions to seperate method to improve readability.
        2. Magic values
            the user role comparison with env('ADMIN_ROLE_ID') and env('SUPERADMIN_ROLE_ID') use a magic valuse. you can considering to use configuration files or constant in model for a better maintainability.
        3. Code duplication
            some loginc, especcially related to handling job data in the "distanceFeed" method is repeated. you can refactor and extract the commont functionality to seperate methods
        4. Exception Handling
            the 'resendsSMSNotifications' method catches all exception without any functionality to handling them specifically. it might be better to handle each diffrent exceptions appropriately
        5. Consistent return types
            there is some method that return a response while other return a null or other type it is better to return more consistent to one type to make code more predictable
2. BookingRepository
    a. What i like
        1. getUserJob
            a. its have a very descriptive variable namse like $cuser, $usertype, etc making the code more easy to understand
            b. the function seems to seperate the concerns by determining the user type and processing it accordingly
            c. the readabality is pretty good and straight forward
        2. getUsersJobHistory
            a. like the first function it uses descriptive variable names wich is good
            b. have pagination handling
            c. its also implement the seperation of concerns
        3. store
            a. also use descriptive variable name
            b. good validation for inputs
            c. conditional logic for handling immediate job and regular job,gender,etc is well organaized and readable
            d. date formatting is handled effectively using Carbon to ensure the fromattying and checking
            e. the function provides a response array that indicating the status of the operation and other relevant information
    b. what to improve
        1. getUserJob
            a. the function has multiple responsibilities like fetching jobs based on user type, catorizing ithem to emergency and normal and also modifying the normal jobs collection. consider to breaking down this function to smaller and more focussed methods
            b. the function mixes the use of array and cocllection consistency in data strycture may can improve the overall clarity of the code
            c. the che for $cuser is done multiple times consider doing this check once at the beginning of the function and returning it early
        2. getUsersJobHistory
            a. The lines $emergencyJobs = array(); and $noramlJobs = array(); are duplicated from getUserJob
        3. store
            a. the validation message nad response structure a repeated you can centralizing this 2 structure or using constant or messages
            b. the conditions to determining gender, certified type, and job type could be simplified or made to become more readable, consider to use mappoing or function for this
            c. there are several commented out linse in code consider to remove them if not longer needed
