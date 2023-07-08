# ColabScan
Making it easier for non-bioinfos to search their data for RdRps.  
   WORK IN PROGRESS!!!   
   
### TO DO:  
1. ADD THE TO DO List to here...  
2. Split the workflow into two notebooks:   
          *a*. Preprocess - downloads all data (various RNA virus resources NeoRdRp, RVMT, RdRp-Scan, PalmDB), bundles it, maybe deduplicates it, and builds an hmmdb + mmseqsdb +blastdb + whatever. Final step is periodical/on-change deposit in a continous Zenodo repo for archivability/reproducibilty and data (as opposed to code) versioning.  
          *b*. Search - A simplistic "scan" workflow; Takes the user input contigs as a single multifasta file, converts the input nucleic seqs into amino seqs, downloads the DBs from a.'s Zenodo, install the needed search tools on the runtime, and finally searches the for cool bugs.  
          Both a. and b. will be availble from this repo, where we'll accept pull requests adding data-resources to a. 
          
Note!! The output of b. is not intended to be a conclusive or definitive "last word" about anything, only the hmmsearch/search-tool output (match coordinates, alignment statistics etc) providing no metadata apart from the match name and the information on which resources the hits came from - it is there for the user responsibilty to go to (and maybe cite?) the original resource to look for the metadata they provided.

### Caveats:  
1. "More is not always better":  
*a*. It is very likely that diversifying the subject set of a search can yield more hits that could have been missed otherwise. However, more HMMs doesn't (necceraily) mean more diveristy. There can be a "dimisnhing returns" thing going on here.   
*b*. Regardless of how anyone defines true/false negatives/positives, aggregation of results is oblivious to which hits are what - so keep in mind, you may also have more false positives.
2. No guarentee that matches are ground trouth level of real actual viruses!  
 Everyone tries to reduce the number of false positives/negatives in their tool/DB/etc, but there is no (*for now!!!*)  no consensous on what is a true/false positive/negative, and different people have a different idea of what cutoffs/evidence are to be considered "stringent" and what are to be considered "promiscus". I make no claims that this "aggregation" approch would only give you true positives, even if you do use highly stringent alignment statistic cutoffs - among else because as anything in life this is a "garbge in garbge out" thing - consider having a perfect match between your input sequence to e.g. what someone thought was an RdRp but is actually a reverse transcriptase (false positive) or an nrEVE (no consenous are they false positives) - You'd need to consider the hits critacly based on your own set of definitions and maybe other lines of evidence (e.g. was the input extracted from total RNA or from a ds-RNA enrichment? are there any other viral genes in close proximity? can you find high-identity matches between your sequence and potential hosts or DNA entites?). Right now, this ColabScan idea makes no attempt to call the shots on such matters.
3. From a computation/total-runtime prespective this doesn't make any sense - but that's totally fine!    
This is intended for people who (rightfully) do not have the time to go over each and every new DB, learn how to write and run code for each, or get familiar with the various quirks of homology searches at large. Every time you intitate the ColabScan notebook it installs all the dependencies (e.g. hmmer and seqkit) from scratch (using resources) and fetching the DBs (using network bandwidth). We are reling on Google good graces assuming this wouldn't use much resources so we can get this search done via their free tier. If you plan on using this multiple times or for large assemblies, I suggest downloading and trying to run it via  [jupyter-lab](https://jupyter.org/install) in a seprate conde/venv/something. We might add a seperate code/notebook for running this locally, if there is any want for this.

### Contribute
Please do! pull-requests are 100% welcome.   
Coders - I'm a self addmitted bad programer, refactors welcome.  
Potential users - testers needed!!! this is designed for you so we need your feedback!  
Tool makers - add your tool.  
DB makers - add your DB.


### Closing remarks
I've decided to make this upon hearing from more and more wet-lab researchers that they keep missing the viruses in their samples if they are only using the tool that is the easiest to use "off the shelf". Giving way to a single tool/approach to monopolise a research niche is (IMO) dangerous. It can make other tools/approaches results be considered by default less reliable just because of lower adoption rate (and not on scientific content grounds). The final nail in the coffin for making this was that I was standing in front of a poster presented by an extremely talented experimentalist (that is also familiar with bioinfo!) who sequenced her dsRNA extractions and shared that the off-the-shelf tool didn’t identify half or so of the sequences she can *experimentally demonstrate* are de-facto viruses, while running an HMM based method was able to help (even though only one such alternative approach was tested..)




