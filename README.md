# RPA-Description
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html lang="en">
<body>
<header>Description of the RPA user stories</header>
<ol>
   <li>Connect Buergel ID and add relation with Creditshelf</li>
   <ul>
        <li>given an Excel extract: all companies that did not have a Buergel ID were supposed to get connected</li>
        <li>match only if name, legal form, city/zip code and 100% matching</li>
        <li>all companies not having a relation with Creditshelf should be edited to "Partner" (Banken, Steuer-/Unternehmensberatungen, Versicherungen, Wirtschaftsprüfungen) or "Kreditnehmer" (everyone else)</li>
	      <li>Bot ran once going through all remaining companies</li>
    </ul>
    
   <li>Adjust companies blacklist reasons according to cluster</li>
   <ul>
	    <li>7014 companies and 163 people with blacklist reasons</li>
	    <li>new cluster to get more consistency (suggestions from TLS)</li>
	    <li>Bot deleted the old blacklist reason and entered the new reason from clustered list</li>
	    <li>cleaning for all 7014 companies took 5,5 hours, 163 people in 10 minutes in total</li>
	    <li>should be run regularly, as new entered blacklist reasons are inconsistent</li>
	    <li>alternatively: drop down menu for entering blacklist reasons</li>
   </ul>
   <li>Set companies with empty relation to "Partner" (prior to  30.04.2020)</li>
   <ul>
	    <li>adjustment of the first Bot (automatically set partner for all companies in list)</li>
	    <li>3258 companies were adjusted in three hours</li>
	    <li>issue: 105 companies having "potential" field filled in could not be changed, deletion of this field required</li>
   </ul>
   <li>Delete companies websites that are wrong according to Regex</li>
   <ul>
      <li>from all companies having a website checked correctness with Regex</li>
      <li>Bot corrected those entries marked as wrong according to Regex</li>
      <li>40000 companies in total in about 35 hours</li>
      <li>issue: for 586 companies entries like "http://NA" and "http://" cannot be deleted</li>
      <li>deletion of these in discussion</li>
      <li>originally also planned for people but turned out irrelevant there</li>
   </ul>
   <li>Validate Address data and change country, city and/or zip code for people and companies</li>
      <ul>
          <li>for all companies/people with wrong or missing city or zip code or country</li>
          <li>python package "geopy" for invalid zipcodes to check correctness</li>
          <li>and introduce consistent versions for cities</li>
          <li>extract countries from email and website endings</li>
          <li>set up four EC2 instances as the bots ran through all companies and people for better quality </li>
          <li>226507 companies were adjusted in 56 hours running on all four instances</li>
          <li>2631 people were corrected in 2,5 hours with the same  procedure</li>
      </ul>
   <li>Correct Salutations</li>
      <ul>
          <li>all people with wrong or missing salutation should be filled (through research)</li>
          <li>144 people were corrected in under ten minutes</li>
      </ul>
   <li>Correct wrong Email addresses according to Regex</li>
      <ul>
          <li>all people with wrong email addresses (Regex)</li>
          <li>according to the check only 25 companies have wrong email addresses, but an additional 31420 have "NA"</li>
          <li>bot deleted these and corrected the remaining</li>
          <li>21 hours for 31444 people</li>
      </ul> 
   <li>Link Buergel, Crefo and Kantwert for companies with credit project or blacklist reason</li>
      <ul>
          <li>given all borrowers with at least one missing ID</li>
          <li>bot should connect Buergel, Crefo and Kantwert</li>
          <li>for Buergel: comparison only with the percentage given in the CSP</li>
          <li>for Crefo: compare company name, zip code and street</li>
          <li>for Kantwert: data already filtered in CSP, therefore always connect if a match was found</li>
          <li>approximately 2400 companies connected by the bot, quite a lot remaining cases which had to be done manually</li>
      </ul> 
   <li>Remove  Partners without client protection from borrowers</li>
      <ul>
          <li>916 companies from a given list had to get the fields testimonial_company_id & testimonial_person_id removed</li>
          <li>took 5 hours for all companies</li>
     </ul> 
</ol>
</body>
</html>
