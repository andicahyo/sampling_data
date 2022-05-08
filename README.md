# sampling_data
digunakan untuk sample data dari data github weather_data.xlsx

langkah langkah yang dilakukan meliputi: 

# Mendowload data dan disimpan di terminal lokal dulu
wget -P ./data https://github.com/labusiam/dataset/raw/main/weather_data.xlsx


# Masuk ke folder data dimana tempat file berada 
cd data 

# convert di masing masing sheet yang ada di file weather_data.xlsx dan disimpan
# di file csv 

in2csv weather_data.xlsx --sheet 'weather_2014' > weather_2014.csv
in2csv weather_data.xlsx --sheet 'weather_2015' > weather_2015.csv

# gabung data yang sudah berbentuk csv tadi menjadi satu file bernama weather.csv
csvstack weather_2014.csv weather_2015.csv > weather.csv

# Hapus file xlsx yang diawal download pada folder data 
rm weather_data.xlsx 

# langkah terakhir sampling data dengan -r 0.3 yang tadi sudah dibuat pada folder data 
cat weather.csv | sample -r 0.3 > sample_weather.csv
