# dallas-shooting
A visualization of police shooting in dallas

I imported the libraries needed for this project which include sqlite3, pandas and matplotlip.

I connected to sqlite database using #sqlite3.connect

The data was read into a DataFrame using pandas

I explored the length of the dataset using the len function.

A new dataset was created subject_incident as officers joined with incidents.

Then i created a new dataset with the features; race, subject_status latitude and longitude and i also dropped all the missing data.

For me to be able to visualize, race column was converted by mapping;

mapping = {'B':'blue', 'W':'yellow', 'A':'red', 'L':'green'}

dataset['race'] = dataset['race'].apply(lambda X:mapping[X])

and the subject_status
mapping = {'Deceased':1000, 'Injured':500, 'Shoot and Miss':250}

dataset['subject_statuses'] = dataset['subject_statuses'].apply(lambda x:mapping.get(x, 100))

I visualized the data by making a scatter plot ;

dataset.plot.scatter(x='longitude', y='latitude', s='subject_statuses', c='race', title='Dallas shooting' , alpha=.6)
