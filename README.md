# Programming-Fundamentals-2
# Assignment 2 - Pet DayCare Management System

# Student Name: Nathan Dolan
# Student Number: 20059337

# Chronology of your implementation (what you did first, etc.. )

1. I started this assignment by following the plan of action provided to me in the assignment specification. I looked at the 'models' first and decided to start with the superclass 'Pet'.
We declared that 'Pet' was a class that belongs to the model package before then declaring it as an abstract package.

Next we created our fields such as int Id, String name, String   owner etc. We then moved on to creating our constructor for the 'Pet' class which was used to set initial values for object attributes. After creating our constructor we focused on our setters and getters which would be required to take in information via getters from the user before checking that they meet the rules provided by the setters.

Laslty, we created an abstract method which future subclasses (Dog, Cat, Misc) would need to implement in order to calculate the weekly fee.

2. Next we looked at creating the subclasses that would extend from the 'Pet' superclass and so we decided to start with 'Dog'. Again we started by declaring that 'Dog' was a class that belongs to the model package before creating the class 'Dog' and making it an extension of 'Pet' meaning that it inherits all the properties and behaviours of the 'Pet' superclass. We went on to create the pricing for dogs who were dangerous and non-dnagerous which were to be constants. We used the variable "final" to ensure that the values could not be changed.

Next we created our fields such as String breed, boolean dangerousBreed and boolean neutered. We then moved on to creating our constructor for the 'Dog' class which would use the keyword 'super' to call on the 'Pet' constructor to set common properties before given our variables values. After creating our constructor we focused on our setters and getters which would be required to take in information specific to dogs, via getters, from the user before checking that they meet the rules provided by the setters. 

To finish off this class we were required to implement the methods calculate weekly fee which would take in information on whether the dog was dangeorus or not and the number of days were attending before calculating a price and the toString() method which would take in information in relation to what days the dog would be in attendance. For these methods we used the @Override annotation in order to help catch any errors that may arise.

3. Next we looked at creating the subclass 'Cat'. Again we started by declaring that 'Cat' was a class that belongs to the model package. But before creating the class 'Cat' and making it an extension of 'Pet' we needed to import the CatToyUtility class from the utils package as it was required to validate cat toys information input by the user.

Next we created our fields such as String favoriteToy and boolean indoorCat. We then moved on to creating our constructor for the 'Cat' class which would use the keyword 'super' to call on the 'Pet' constructor to set common properties before given our variables values. After creating our constructor we focused on our setters and getters which would be required to take in information specific to cats, via getters, from the user before checking that they meet the rules provided by the setters. 

To finish off this class we were required to implement the methods calculate weekly fee which would take in information on whether the cat was an indoor cat or not but instead of setting the price values the start of the class we decided to add the value to our calculate weekyl fee method and add a surcharge if the cat was an indoor one. 

Then we multiplied that number by the number of days they were attending before calculating a price. Laslty, we implemented the toString() method which would take in information in relation to what days the cat would be in attendance. For these methods we used the @Override annotation in order to help catch any errors that may arise.

4. Next, we looked at creating the main controller class, DayCare, which would manage all the pets, reporting, statistics, and data persistence for the pet daycare system. We started by declaring that DayCare belonged to the controllers package and then imported the necessary classes, including input/output utilities, ArrayList for storing pets dynamically, XStream for XML serialization, and all classes from the models package so we could work with Dog, Cat, Misc, and Pet objects. We then moved on to defining the fields for the class. These included an ArrayList<Pet> to store all registered pets, an integer maxNumberOfPets to limit the number of pets in the daycare, a String name for the daycare's name (truncated to 20 characters if too long), and an Object maxPets as a temporary holder when loading data from XML.

Next, we created the constructor for DayCare, which would initialize the daycare's name, maximum pet capacity, and the empty ArrayList of pets. We used a ternary operator to truncate the name if it exceeded 20 characters. We then implemented the CRUD (Create, Read, Update, Delete) methods. Methods like addPet allow new pets to be added if there is space, while deletePetByIndex and deletePetById remove pets either by their position in the list or their unique ID. Similarly, getPetByIndex and getPetById retrieve pets using index or ID, respectively.

After that, we focused on reporting methods, which generate lists of pets in various categories. For example, listAllPets shows every pet, listAllCats, listAllDogs, and listAllMisc filter pets by type, and listAllDangerousDogs only shows dangerous dogs. Additional reporting methods allow filtering by owner with listAllPetsByOwner or by how many days per week a pet attends using listAllPetsThatStayMoreThanDays. We also created statistical methods to count pets in different categories. numberOfPets returns the total number of pets, while numberOfCats, numberOfDogs, numberOfMisc, numberOfDangerousDogs, and numberOfIndoorCats provide counts based on type or characteristics. These methods help summarize the daycare's population at a glance.

Next, we implemented update methods to modify existing pets. updateDog, updateCat, and updateMisc take an ID and a new object with updated details, replacing the old entry in the list if a match is found.We also added validation methods, like isValidId, to check if a given ID is unique before adding a new pet. For other utility methods, we implemented functions like getWeeklyIncome, which calculates total income from all pets based on their weekly fees, getAllPets to return the full list of pets, getAverageNumDaysPerWeek to calculate the average attendance, and findDogByOwnerAndBreed to locate a specific dog by both owner and breed. getPetsByOwnersName formats all pets belonging to a particular owner for display.

Finally, we handled data persistence using XML. The save method uses XStream to serialize the DayCare object and all pets to an XML file named daycare.xml. Conversely, the load method reads from this file and reconstructs the daycare object, handling missing or empty files as well as XML parsing errors. We carefully configured XStream with aliases and allowed classes to ensure all pets could be saved and loaded correctly, preserving references.

5. Next, we looked at creating the Driver class, which serves as the main entry point for the DayCare application and provides a text-based interface for managing pets. We started by declaring that it belonged to the main package and then imported all the necessary classes, including the DayCare controller, all models (Dog, Cat, Pet), and utility classes (ScannerInput, Utilities, DogBreedUtility, CatToyUtility) to help with user input validation and pet-specific rules. We then declared a static variable dayCare to store the main DayCare instance. This allowed all methods in the class to access and manipulate the same DayCare object throughout the program.

The main method was created as the entry point of the application. Here, we initialized the DayCare object with a name and maximum capacity and set up a main menu loop that continues running until the user chooses to exit. The main menu uses a switch statement to handle user input and directs them to different functionalities, such as the CRUD menu, reports menu, search and sort features, or saving/loading data to and from XML. We then created the main menu display method, showMainMenu, which prints all the options available to the user, including adding, updating, deleting, listing pets, viewing reports, and saving/loading data.

Next, we implemented the Pets CRUD menu through the petsCrudMenu method. This menu allows users to perform operations like adding, deleting, listing, and updating pets. Each menu option is linked to a separate method for clarity and organization. The Add Pet functionality is divided into addPetMenu and pet-specific methods (addDog and addCat). These methods prompt the user for all necessary details, such as name, owner, sex, attendance days, and any type-specific attributes:

- Dogs: breed, dangerous status, and neutered status, validated using DogBreedUtility.

- Cats: indoor status and favorite toy, validated using CatToyUtility.

Once the details are collected, a new pet object is created and added to the DayCare using the addPet method. Messages are displayed to inform the user whether the addition was successful or if the daycare is full. The Delete Pet method, deletePet, allows pets to be removed by their index. It first lists all pets for reference, validates the chosen index using the Utilities class, and then deletes the pet using the DayCare controller. The List Pets method, listAllPets, simply calls the corresponding DayCare method to print a formatted list of all pets.

The Update Pet method, updatePet, allows users to modify an existing pet’s information. It first retrieves the pet by index and then prompts for updated information for common fields (name, owner, sex, attendance days) and type-specific fields depending on whether the pet is a Dog, Cat, or Misc. The updated object is then sent back to the DayCare to replace the old entry using the relevant update method (updateDog, updateCat, updateMisc).

The Reports menu, implemented in reportsMenu, provides multiple reporting options, including listing all pets, dogs, cats, miscellaneous animals, dangerous dogs, indoor cats, neutered dogs, and the total weekly income. This menu loops until the user chooses to return to the main menu, calling DayCare methods to retrieve and display information. The Search functionality, searchPets, allows users to search for pets by owner name, using the DayCare method getPetsByOwnersName to display all matching pets. The Sort Pets feature, sortPets, manually sorts all pets alphabetically by name using a bubble sort algorithm. The DayCare pet list is converted to an array, sorted in-place, and then displayed to the user.

6. Lastly, for extra functionality and to help Patt Purrs with the growth of her business and the eventuality that she would later be adding more animals to her service other than cats and dogs I decided to add a new model class and a new utility class to the program. Following the same layout as the 'Dog' and 'Cat' subclasses I created a 'Misc' subclass. Again we started by declaring that 'Misc' was a class that belongs to the model package before creating the class 'Misc' and making it an extension of 'Pet' meaning that it inherits all the properties and behaviours of the 'Pet' superclass. We went on to create basic daily pricing for Misc animals who were in attendance and this was to be a constant. We used the variable "final" to ensure that the value could not be changed. We would later add a surcharge in the weekly fee calculation for any animal requiring special care.

Next we created our fields such as String type and boolean specialCare. We then moved on to creating our constructor for the 'Misc' class which would use the keyword 'super' to call on the 'Pet' constructor to set common properties before given our variables values. After creating our constructor we focused on our setters and getters which would be required to take in vague information in regards to a range of animals, via getters, from the user before checking that they meet the rules provided by the setters. 

To finish off this class we were required to implement the methods calculate weekly fee which would take in information on whether the animal required special care or not and the number of days they were attending before calculating a price and the toString() method which would take in information in relation to what days the animal would be in attendance. For these methods we used the @Override annotation in order to help catch any errors that may arise.

7. After creating our model class it was now time to create our MiscAnimalUtility which would be imported to the Misc class in order to validate the name of the animal being input. This followed the same layout as the DogBreedUtility which started by declaring that the class was part of the utils package. Next we went on to importing the java.util.Hashset and java.util.set which allowed HashSet class to be used to quickly to add, remove, and check items. 

Next we named our class MiscAnimalUtility before creating our field which was a set containing multiple animal types, stored in uppercase, which could be added too whenever a new type of animal was to be introduced to the service. Then to finish the util class we added a method to check the type of animal that was being entered into the service, returning a false if the input was invalid.

# Main difficulties you came across in your development of solution and how you solved them.
1. Subclasses constructors not automatically inheriting the Superclass constructor was an issue I faced at the very beginning of creating this code. After going back through my class notes and conducting reasearch @ https://www.w3schools.com/java/ref_keyword_super.asp I realise I needed to add super() to call Pet constructor to set common properties.

2. System was not calculating the weekly fee correctly. The system kept calling the Pet's method instead of method for the Subclasses. After researching @ https://www.w3schools.com/java/java_annotations.asp and going back through class notes I realised I need to add the @Override annotation in order for the system to call on the 'Dog' subclass to calculate the weekly fee for a dog, for the system to call on the 'Cat' subclass to calculaye the weekly fee for a cat, etc.

3. Saving and loading information to Xstream presented me with a few errors and, even though the file would sometimes say the information was saved correctly or loaded correctly, there would be no information available on the page. Again, after doing research @ https://www.w3schools.com/java/java_try_catch.asp and by going through class notes I was able to work my way through the issues and create a functioning method.

# Any bugs remaining in the solution or unfinished elements of spec

1. When Saving information I am met with these warning messages and am unsure on how to fix them. The programme still saves the information correctly regardless:
- WARNING: A terminally deprecated method in sun.misc.Unsafe has been called
- WARNING: sun.misc.Unsafe::objectFieldOffset has been called by com.thoughtworks.xstream.converters.reflection.SunUnsafeReflectionProvider (file:/C:/Users/natan/Downloads/KennelCare_Starter/KennelCare_Starter/src/utils/xstream-1.4.21%20(1).jar)
- WARNING: Please consider reporting this to the maintainers of class com.thoughtworks.xstream.converters.reflection.SunUnsafeReflectionProvider
- WARNING: sun.misc.Unsafe::objectFieldOffset will be removed in a future release
   
2. When Loading information I am met with these warning messages and am unsure on how to fix them. The programme still loads the information correctly regardless:
- WARNING: A terminally deprecated method in sun.misc.Unsafe has been called
- WARNING: sun.misc.Unsafe::objectFieldOffset has been called by com.thoughtworks.xstream.converters.reflection.SunUnsafeReflectionProvider (file:/C:/Users/natan/Downloads/KennelCare_Starter/KennelCare_Starter/src/utils/xstream-1.4.21%20(1).jar)
- WARNING: Please consider reporting this to the maintainers of class com.thoughtworks.xstream.converters.reflection.SunUnsafeReflectionProvider
- WARNING: sun.misc.Unsafe::objectFieldOffset will be removed in a future release
   
3. On completion of the assignment I went back through the assignment specification and realised I had never created a checkIn or checkOut Method. Due to time constraints I was unable to work these in and have them functioning correctly and so I was forced to leave them out.

# Main learnings from your engagement with assignment
1. One of the main learnings I recieved from this assignment was how to use operators to neatly clean up code and shorten it to make it present nicer. Throughout my assignment you will notice th use of operators such as !, ?, &, : and || to help tidy up methods.

2. The use of XML to save and load information was another big piece of learning for me as it was something I had never come across before. Although I met with multiple issues when trying to get in working I found it very rewarding when I finally managed to get it workinng. I also now understand that saving and loading of information is what is now known as persistence.

3. Inheritence was a massive part of this assignment and again something I had never done before. Learning how subclasses can be used as extensions of their superclass was very enlightening. Ensuring that the subclasses were calling on the superclass in relation to constructors was one of the main challenges I faced when completing this assignment but after resaerching into the matter it became one of my biggest pieces of learning from it.

4. Lastly, the use of utils to help ensure that information is validated when a programming was running was new to me. Being able to create utilities and understand how they function was a skill I developed from working on this assignment. Creating the MiscAnimalUtility after learning from the likes of the DogBreedUtility to have the system validate the typer of animal being enetered into the system was evidence of my learning throughout.

# Answer the following questions:
1. Pat Purrs mentioned a problem their friend had with their pet system. What was the issue with that system, and how is your design intended to avoid the same problem?
- Patt Purrs friend found that when she was creating her own website that all the code was written into one giant class with no clear model or controller and was tightly linked to the controller interface meaning that when the site needed editing or changing that then whole code had to be written from scratch. My design is much different as it is separated into a multiple packages with multiple classes, some which are extensions of other classes or have classess imported into them. This means that if any changes need to be made that it would require only small changes to a singular class to do so and that if the site needed updating to add new animals that it can be done so with eases by adding a new class to models and make slight adjustments to the coding in driver, controller. 
     
2. Why does Pat want the Driver class to be simple and user-friendly, and how does this relate to the plan to eventually develop a mobile app?
- So that staff can, with ease, register new pets, identify whether they are a cat, dog or mis, record pet detials, see which pets are currently in the daycare, see who is/isn't neutered, etc.
- Patt Purrs wants the driver to be well organised and structured so that it won't require any changes when being used to create the mobile application. If the driver is in its own package "main" rather than in one big class that it can be transferred with eased.
     
3. Pat talked about future expansion of the daycare. What kinds of growth does the system need to support, and how should your code design accommodate this?
- Patt Purrs expects there to be an increase in the number of animals coming into the service and would like a system that is able to handle this increase in numbers. Ensuring that there is no hardcoded limitations in the coding is very important as the system needs to be flexible to allow for any number of new pets to be entered into the system. Using the ArrayList <Pet> I was able to have the system store all the information in regards to the pets registered in the day care. Removal of any maximum pet limitations allows for the number of pets to be stored to be unlimited.
     
4. Besides cats and dogs, what additional animal does Pat plan to include next, and what does this imply for how you structure your inheritance hierarchy?
- Patt Purrs stated that in the future she would like to accomodate rabbits but also mentions possibly taking in Alpacas, Ferrets, etc.
- Going forward Patt will be able to use the Pet class as her superclass and any animal specific class can be used as a subclass which extends upon the Pet class. For ease for Patt Purrs I have already created a Misc class which has mutliple types of animals on it with room to add more with ease. If Patt would like to take one of these animals and make them a subclass of her own then she can do so with ease by following the layout of the Dog or Cat classes.

# Mandatory : Please list any references used in your development/ implementation of your submission. 
1. Helping me to understand my usage of the keyword 'super' I used the site: https://www.w3schools.com/java/ref_keyword_super.asp
2. Helping me to understand my usage of the variable 'final' I used the site: https://www.w3schools.com/java/java_variables.asp
3. Helping me to understand my usage of the 'constructor' method I used the site: https://www.w3schools.com/java/java_constructors.asp
4. Helping me to understand my usage of the statements 'try' and 'catch' I used the site: https://www.w3schools.com/java/java_try_catch.asp
5. Helping me to understand my usage of the '@Override' annotation I used the site: https://www.w3schools.com/java/java_annotations.asp
6. Helping me to understand my usage of the 'HashMap' I used the site: https://www.w3schools.com/java/java_hashmap.asp
7. Helping me to understand my usage of the 'HashSet' I used the site: https://www.w3schools.com/java/java_hashset.asp
8. Helping me to understand my usage of the keyword 'case' I used the site: https://www.w3schools.com/java/ref_keyword_case.asp
9. Helping me to understand my usage of the 'switch' statement I used the site: https://www.w3schools.com/java/java_switch.asp
10. Helping me to understand my usage of the operators such as '!, ?, &, :, ||, etc' in boolean comparisons I used the site: https://www.datacamp.com/doc/java/java-booleans
11. I learned from doing a bit of research that it was poaaible to import all classes in a package at once by using the operator * e.g import models.*; from this site: https://docs.oracle.com/javase/tutorial/java/package/usepkgs.html
12. I learned what a ternary operator was from doing research on how to clean up code from this site (specifically Example 3): https://www.geeksforgeeks.org/java/java-ternary-operator/

# Please consider the following statements and choose one (delete the inappropriate one)

- This is my work apart from the specific references noted above (and any code from class notes). I understand the code and can decribe any parts of the solution if needs be;



