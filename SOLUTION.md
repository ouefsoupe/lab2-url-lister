Solution Explaination:
For the url count I copied all the logic exept for the tokenizer(and one small change to the main function). The change I made in the tokenizer was instead of iteratorating over every word I used a regex matcher. This matcher works like an iterator except instead of splitting on spaces each next iteration is a match for the regex pattern I defined. Each time a match is found it is added to the context map where the key is the matching string within the quotes of the href and the value is the constant 1. This means at the end of the tokenizerMapper funciton context will be a map of all links with a one as their value, at this point there can be duplicates. The IntSumReducer method then combines the counts of the matching links. That way the final return has no duplicates and rather has accurate counts.

For 1 master and 2 workers:
real    0m57.882s
user    0m9.935s
sys     0m0.635s

Output:
/wiki/MapReduce 7
mw-data:TemplateStyles:r1295599781      33
/wiki/Google_File_System        6
mw-data:TemplateStyles:r1238218222      121
mw-data:TemplateStyles:r886049734       12
/wiki/Doi_(identifier)  18
/wiki/ISBN_(identifier) 18
/wiki/S2CID_(identifier)        14
mw-data:TemplateStyles:r1129693374      7

For 1 master 4 workers:

real    1m3.764s
user    0m13.792s
sys     0m1.054s

Output:
/wiki/MapReduce 7
mw-data:TemplateStyles:r1295599781      33
/wiki/Google_File_System        6
mw-data:TemplateStyles:r1238218222      121
mw-data:TemplateStyles:r886049734       12
/wiki/Doi_(identifier)  18
/wiki/ISBN_(identifier) 18
/wiki/S2CID_(identifier)        14
mw-data:TemplateStyles:r1129693374      7
