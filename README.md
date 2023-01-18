# Service for targeted design of selective non-toxic antibacterial nanoparticles
The goal of this project is to create a service that designs inorganic nanomaterials with selective cytotoxicity and antimicrobial properties. To achieve this, we plan to integrate an evolutionary method with a machine learning approach to optimize the properties of antimicrobial nanoparticles.
## Description
### Problem
Antibiotic resistance (AR) is a major threat to global health, food security, and development. It can affect individuals of all ages and in any country. While it occurs naturally, the misuse of antibiotics in humans and animals is accelerating the process. A growing number of infections such as pneumonia, tuberculosis, gonorrhea, and salmonellosis are becoming harder to treat as the antibiotics used to treat them become less effective. The numbers speak for themselves: bacterial resistance has increased by 10% on average over the past 20 years and over 50% of commonly used antibiotics are no longer effective. Additionally, only one new class of antibiotics has been discovered in the last 35 years. Humanity needs a better weapon against pathogens.
### Solution
Nanoparticles (NPs) are increasingly being used as an alternative to antibiotics for targeting bacteria. Nanotechnology may be particularly advantageous in treating bacterial infections. Examples include the use of NPs in antibacterial coatings for implantable devices and medicinal materials to prevent infection and promote wound healing, in antibiotic delivery systems to treat disease, in bacterial detection systems to generate microbial diagnostics, and in antibacterial vaccines to control bacterial infections. The antibacterial mechanisms of NPs are not fully understood but currently accepted mechanisms include oxidative stress induction, metal ion release, and non-oxidative mechanisms. The multiple simultaneous mechanisms of action against microbes would require multiple simultaneous gene mutations in the same bacterial cell for antibacterial resistance to develop; therefore, it is difficult for bacterial cells to become resistant to NPs. This is why nanoparticles can be a promising solution to this problem.
### How should it work?
Genetic algorithms (GAs) are a relatively new optimization technique that mimic the evolution of a species according to the Darwinian theory of “survival of the fittest”. This algorithm is increasingly being used in the chemical industry but has not yet been applied in the search for antimicrobial nanoparticles. By combining GAs with machine learning, we can accelerate the process of finding nanomaterials with the best antimicrobial properties. The main steps of the project are: collecting data from open sources, data preprocessing, using machine learning for prediction of toxicity against selected microorganisms, optimizing the model, and predicting feature/parameter optimization.
### Proof-of-concept
- The accuracy and reproducibility of the results will depend on the amount and quality of the data. An adequate amount of data with necessary parameters will be gathered during the research.
- The model will be validated experimentally by synthesizing nanomaterials with predicted best features and will be tested in targeted microbial cultures.
- The potential of the research is immense because with enough data the algorithm could predict nanomaterials that can have selective toxicity against any kind of microorganisms which could help cure microbial diseases and infections more effectively.
### Why is it possible:
- Necessary data can be extracted from literature and available on online data repositories. There are certain rules in the scientific style due to which the articles are composed of the same type. They present similar data on the basis of which predictions can be made. The necessary data can be found in the same chapters of the articles making data parsing easier.
- There are special libraries connected to Python, which makes it more convenient for chemical and medical applications, like PyBioMed, Chemlib, ChemSpiPy, etc. and also program packages like ChemML and more.
- Different ML models are available and we will evaluate all of them to find the most suitable model for this particular project.
There is also GitHub, where anyone can find open source code.
## Files
**Antibac_NPs.ipynb** - main notebook with all code (Python was used);
**db_antibac_nps.csv** - main database with 17 columns and 5327 rows;
## Database
There are 17 columns (parameters) in the database:
+ **pathogen** - name of the pathogen species on which the particular nanoparticle was tested;
+ **strain** - name of the pathogen (bacteria) strain on which the experiment was carried out in the literature source;
+ **composition** - composition of the nanoparticle used as a antibacterial agent;
+ **shape_np** - shape of the nanoparticle;
+ **coating** -	nanoparticle coating composition. 'None' means that no coating was applied to the nanoparticle;
+ **coating_n**	- number of coatings applied to the nanoparticle;
+ **mono_poly** - parameter reflecting whether the coating is a	monomer (mono) or polymeric (poly);
+ **molar_mass** - 	molar mass of the nanoparticle, g/mol;
+ **molar_volumes** -  average of the molar volumes of the elements that form the nanoparticle, m3/mol;
+ **electronegativities** - average of the electronegativities of the elements that form the nanoparticle, Pauling units;
+ **polarizabilities** - average of the polarizabilities of the elements that form the nanoparticle, α(C m2/ V);
+ **size_np**	- average size of the nanoparticle, nm:
+ **time** - times of experiment duration t(h) = 2, 5, 18, or 24 hours;
+ **references** - link to the article from which the information in the row was taken;
+ **f(n,c,j,s)obs**	- a parameter reflecting whether the nanoparticle is suitable for a particular bacteria or not; the parameter is equal 1 when the biological activity exceeds the threshold, then the concentration should be minimized. The value is also 1, when the biological activity is below the threshold, then the concentration should be maximized, otherwise this parameter is equal 0;
+ **concentration**	- concentration type from the list below:
  + **MIC (uM)** - *Minimum inhibitory concentration* - the lowest concentration of an antibiotic that prevents the visible growth of bacteria. The concentration at which the nanoparticle inhibits bacterial growth by 50%;
  + **MBC (uM)** - *Minimum bactericidal concentration required to kill 99.9% of the bacterial population* - the minimum inhibitory concentration, or the lowest concentration of the nanoparticle that inhibits bacterial growth;
  + **IC50 (uM)** - *The half maximal inhibitory concentration* - the minimum bactericidal concentration, or the lowest concentration of the nanoparticle that kills the bacteria;
  + **Microb-Eff** - *Microbicidal effect fraction*;
+ **biological_activity** - the biological activity of the NP-system on the assay;
## Other important information
### How should the final service work?
As an input, the user enters information about the pathogen (species, strain), as a predicted value they get information about the most suitable nanoparticle against this pathogen (nanoparticle parameters: composition, shape, size, concentration). 
### At what step is the project right now?
At this step, preprocessing, exploratory data analysis was done, Random Forrest Regressor was chosen as the optimal model. The general model was trained and also individual models for each bacteria. **Leave-one-out CV** was used for a validation. **One-hot encoding** was applied to all those columns where the values are not in numbers.
### What are the next steps?
+ The database needs to be enlarged, because now there is enough data for only two bacteria - Pseudomonas aeruginosa and Escherichia coli;
+ Writing a genetic algorithm and combining it with the ML;
+ Optimization;
+ Backend and frontend of a service; article writing;
### Problems I faced while working on this project
+ There are too many duplicates in the database, but nevertheless the number of repetitions has become quite an important factor later on. Even judging logically, the more times the experiment was repeated and its result was confirmed, the more reliable this data is when compared with those that were obtained as a result of one experiment;
+ There were gaps in the particle shape and coating columns, which I was able to fill in later;
+ After removing duplicates, the number of rows decreased by more than 10 times.
# References
The database was taken from the article: *Ortega-Tenezaca, B., & Gonzalez-Diaz, H. (2020). IFPTML Mapping of Nanoparticles Antibacterial Activity vs. Pathogens Metabolic Networks. Nanoscale.* doi: [10.1039/d0nr07588d](https://doi.org/10.1039/D0NR07588D) 
