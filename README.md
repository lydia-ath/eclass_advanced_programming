Σύστημα Διαχείρησης Σχολικής Μονάδας
==============================================================================================================
Πεδίο προβλήματος: 

* Tο σύστημα θα υποστηρίζει μια σχολική μονάδα μεσης εκπαίδευσης (γυμνάσιο).
* Tο σύστημα θα έχει τη δυνατότητα καταχώρησης-εγγραφής μαθητών-καθηγητών (όνομα, επώνυμο, φύλο, διεύθυνση κατοικίας κτλ).
* Tο σύστημα θα έχει τη δυνατότητα  διαγραφής μαθητών-καθηγητών από το σύστημα (οριστική διαγραφή, επανεγγραφή ή απλή διόρθωση/ενημέρωση στοιχείων).
* Το σύστημα θα καταχωρεί τους μαθητές σε αίθουσες συγκεκριμένης χωρητικότητας (15 άτομα)  λόγω των μέτρων της πανδημίας, οπότε όταν μια αίθουσα γεμίζει οι 
υπόλοιποι μαθητές τοποθετούνται στην επόμενη κτλ.
* Το σύστημα θα κάνει αυτόματη ανάθεση μαθητών σε τμήματα των 15 ατόμων.
* Η γραμματεία θα έχει δυνατότητα καταχώρισης των μαθημάτων για κάθε τάξη (1η, 2α, 3η γυμνασίου).
* Το σύστημα θα υποστηρίζει συγκεκριμένες ειδικότητες Μαθηματικά, Φιλολογικά, Φυσικές Επιστήμες, Φυσική Αγωγή 
και Καλλιτεχνικά.
* Το σύστημα θα υποστηρίζει ανάθεση καθηγητών για διδασκαλία των μαθημάτων του κάθε τμήματος.
εξασφαλίζοντας την συμβατότητα μεταξύ μαθήματος και ειδικότητας καθηγητή καθώς και το μέγιστο ωράριο του 
κάθε διδάσκοντας (20 ώρες).
* Το σύστημα θα υποστηρίζει την καταχώριση βαθμολογίας για συγκεκριμένο μάθημα και τμήμα από διδάσκοντά του
* Το σύστημα θα εκδίδει αναφορές με τη βαθμολογία κάθε μαθητή.



Οικοδόμηση 
---------------------------------------------------------------------------------------------------------------

Η οικοδόμηση (build) του λογισμικού γίνεται με το εργαλείο [Maven 3](https://maven.apache.org/)
Η εγκατάσταση του Maven είναι σχετικά απλή. Αφού κατεβάσουμε το Maven (π.χ. έκδοση 3.5.0) και τα αποσυμπιέσουμε σε κατάλληλους καταλόγους 
π.χ. <code> C:\\Program Files\\apache-maven-3.5.0\\ </code> αντίστοιχα θα πρέπει:

* να ορίσουμε τη μεταβλητή περιβάλλοντος JAVA_HOME η οποία θα δείχνει στον κατάλογο εγκατάστασης του JDK,
* να προσθέσουμε τον κατάλογο <code> C:\\Program Files\\apache-maven-3.5.0\\bin </code> στη μεταβλητή περιβάλλοντος PATH.
* να ορίσουμε τη μεταβλητή περιβάλλοντος M2_HOME. Στο παράδειγμά μας είναι ο κατάλογος <code>C:\\Program Files\\apache-maven-3.5.0\\</code>.

Για να εκτελέσουμε από τη γραμμή εντολών εργασίες οικοδόμησης του λογισμικού χρησιμοποιούμε το Maven μέσω της εντολής <code>mvn</code>, 
αφού μετακινηθούμε στον κατάλογο όπου βρίσκεται το αρχείο pom.xml. Η τυπική εκτέλεση του Maven είναι:

<code>mvn [options] [target [target2 [target3] … ]]</code>

Τα παραγόμενα αρχεία δημιουργούνται από το Maven στο κατάλογο <code>/target</code>. 

Τυπικές εργασίες με το Maven είναι:
* <code>mvn clean</code> καθαρισμός του project. Διαγράφονται όλα τα αρχεία του καταλόγου <code>/target</code>.
* <code>mvn compile</code> μεταγλώττιση του πηγαίου κώδικα. Τα αρχεία <code>.class</code> παράγονται στον κατάλογο <code>/target/classes</code>.
* <code>mvn test-compile</code> μεταγλώττιση του κώδικα ελέγχου. Τα αρχεία .class παράγονται στον κατάλογο <code>/target/test-classes</code>.
* <code>mvn test</code> εκτέλεση των ελέγχων με το JUnit framework. 
* <code>mvn site</code> παραγωγή στο site του έργου το οποίο περιλαμβάνει την τεκμηρίωση του έργου.
* <code>mvn umlet:convert -Dumlet.targetDir=src/site/markdown/uml</code> παράγει αρχεία εικόνας png για όλα τα διαγράμματα που βρίσκονται στην τοποθεσία `src/site/markdown/uml`. Συστήνεται η κλήση της εντολής πριν την υποβολή μιας νέας έκδοσης διαγραμμάτων στο git repository (`git commit`). Ως αποτέλεσμα τα παραγόμενα αρχεία εικόνας των διαγραμμάτων συνοδεύουν τα πηγαία αρχεία έτσι ώστε να είναι εύκολη η πλοήγηση στην τεκμηρίωση του project  μέσω του github.

Η τεκμηρίωση περιλαμβάνει:
* Ένα πρότυπο εγγράφου προδιαγραφών απαιτήσεων λογισμικού. Τα πηγαία αρχεία του εγγράφου βρίσκονται στον φάκελο <code>/src/site</code>.
* Το έγγραφο περιγραφής σχεδίασης λογισμικού. Τα πηγαία αρχεία του εγγράφου βρίσκονται στον φάκελο <code>/src/site</code>.
* Η τεκμηρίωση του κώδικα με το JavaDoc.
* Αναφορές καλύψεων κώδικα με χρήση του εργαλείου JaCoCo.
* Αναφορά αυτόματης επιθεώρησης κώδικα με το εργαλείο CheckStyle.
* Αναφορά αυτόματης επιθεώρησης κώδικα με το εργαλείο SpotBugs.
* Αναφορά αντιγραφής/επικόλλησης κώδικα με το εργαλείο CPD/PMD.
* Αναφορά αυτόματης επιθεώρησης κώδικα με το εργαλείο PMD.


Eclipse
-------------------------------------------------------------------------------------------------------------
Η εισαγωγή του project στο Eclipse γίνεται με την επιλογή <code>File/Import/Maven/Existing Maven Projects</code> με την επιλογή του καταλόγου που περιλαμβάνει το project.  


Τεκμηρίωση
-------------------------------------------------------------------------------------------------------------
Για την τεκμηρίωση του λογισμικού χρησιμοποιήθηκε το Markdown markup για τη συγγραφή των κειμένων και το εργαλείο UMLet για την κατασκευή των διαγραμμάτων UML.
 

## Χρήσιμες εντολές:
Η διαχείριση της οικοδόμησης του έργου μπορεί να γίνει με μια σειρά βασικών εντολών:
- `mvn`: εκτελεί τον προκαθορισμένο κύκλο οικοδόμησης
- `mvn test`: εκτελεί τα unit tests του project
- `mvn site`: παράγει την τεκμηρίωση του project σε μορφή HTML. Τα παραγόμενα αρχεία 
  είναι διαθέσιμα στην τοποθεσία `target/site/`
- `mvn umlet:convert -Dumlet.targetDir=src/site/markdown/uml`: παράγει αρχεία εικόνας png για όλα τα διαγράμματα που βρίσκονται στην τοποθεσία `src/site/markdown/uml`. Συστήνεται η κλήση της εντολής πριν την υποβολή μιας νέας έκδοσης διαγραμμάτων στο git repository (`git commit`). Ως αποτέλεσμα τα παραγόμενα αρχεία εικόνας των διαγραμμάτων συνοδεύουν τα πηγαία αρχεία έτσι ώστε να είναι εύκολη η πλοήγηση στην τεκμηρίωση του project  μέσω του github.  
