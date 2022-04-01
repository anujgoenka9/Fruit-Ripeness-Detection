# Fruit-Ripeness-Detection
This project aims to classify 6 types of fruit (apple, banana, orange, pomegranate, mango and papaya) into 3 classes of raw, ripe or rotten

## Data Collection
The model was trained on the dataset that was scraped from Google Images using selenium.

I created a programme that opens a webpage and searches for images. The img tag will be used to identify the photos, and each image will have the CSS selector Q4LuWd. The picture tags are continually added to a list by a function. It then selects the image and searches for the n3VNCb tag. It stores the picture source after it has been located. It continues in this manner until the required number of photos is found. If our application needs more images than those found on the first page, it must use the "Search more results" option. In the event that the number of photos required is not satisfied, we have included it in the software.
