DATA = ../../gen/dataprep/data
INPUT = ../../gen/analysis/input
OUTPUT = ../../gen/dataprep/output

all: $(DATA)/downloaded_data.csv $(INPUT)/private_room.csv $(INPUT)/combined_mean_data1.csv


$(DATA)/downloaded_data.csv: download.R
	mkdir -p $(DATA)
	R --vanilla < download.R

$(INPUT)/private_room.csv: $(DATA)/downloaded_data.csv transform.R
	mkdir -p $(INPUT)
	R --vanilla < transform.R

$(INPUT)/combined_mean_data1.csv: $(INPUT)/private_room.csv clean.R
	mkdir -p $(INPUT)
	R --vanilla < clean.R

$(OUTPUT)/clean_data.rmd: $(DATA)/downloaded_data.csv 
	Rscript -e "rmarkdown::render('clean_data.rmd')"