# Load in R Packages
## Data.table is my preferred data management software (many people use dplyr)
library(data.table)
## Stingr is for regular expressions and string parsing
library(stringr)

# Taking first two words for from each string to establish the species name
data[,SpeciesName:=word(Taxon,1,2,sep=" ")]

# Creating an infra rank for varieties
data[grepl("var.",Taxon, fixed=T),infraRank:="var."]
# Creating an infra name for varities by extracting the first word after "var."
data[grepl("var.",Taxon, fixed=T),infraName:=str_extract(Taxon, '(?<=var\\.\\s)\\w+')]
# Creating an infra rank for subspecies
data[grepl("subsp.",Taxon, fixed=T),infraRank:="subsp."]
# Creating an infra name for subspecies by extracting the first word after "subsp."
data[grepl("subsp.",Taxon, fixed=T),infraName:=str_extract(Taxon, '(?<=subsp\\.\\s)\\w+')]

# The species name is the "Fixed" Taxon name for species level taxa that do not contain "var." or "subsp."
data[!(grepl("var.",Taxon, fixed=T)|grepl("subsp.", Taxon,fixed=T)),TaxonFixed:=SpeciesName]
