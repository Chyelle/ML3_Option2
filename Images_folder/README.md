Chyelle Milgrom
ML_Assignment_3
Option_2: Met Data


Goal: 
I have two visualizations for how the clusters are being analyzed. The first is a sillhouette and the second is a scatter plot. The k-means algorithm reutrns a "silhouette score", the best value is 1 and the worst value is -1. The silhouette visualization should resemble a more box-like shape rather than a triangle. I believe a more rectangular shape indicates more of a strong correlation between points compared to the latter. The scatter plot on the other hand is more explicit in its meaning and the objective is to have points on the plot be placed in denser groups, as that would indicate strong correlation.  

Iteration 1: X = data[['pl', 'si', 'va', 'te', 'co', 'or', 'sh']]
    This iteration considers these attributes:
    pl	given location on the planar dimensions
    si	variations in height, width, area
    va	the various degrees between white and black
    te	variation in the fineness or coarseness of an area having a given value; includes blur
    co	hue, using the repertoire of colored sensations which can be produced at equal value
    or	various orientations, ranging from the vertical to the horizontal in a distinct direction
    sh	a mark with a constant size can nonetheless have an infinite number of different shapes
--> The best Silhouette Score (clusters #5): 0.5647990853234187
--> Human Eye: In examining the art after being clustered I sometimes would find strong correltions between pieces within clusters though often I would find strong outliers and wonder how that became associated with the rest grouping. Nevertheless, the strong correlations may also be pedantic because the shared elements I would find may also be too subtle to have been indicated in the text data. 

Iteration 2: X = data[[ 'country_of_origin','representation', 'representation_semi','spatial_dimension', 'va', 'co','li']]
    This iteration considers these attributes:
    country_of_origin	country of work
    representation	indicates the work represents some aspect of reality
    representation_semi	indicates the work represents some aspect of reality
    spatial_dimension	indicates the work is an object that is occupying physical space in more than 2 dimensions (height in addition to length and width)
    va	the various degrees between white and black
    co	hue, using the repertoire of colored sensations which can be produced at equal value
    li	A LINE signifies a phenomenon on the plane which has measurable length but no area. Is independent of the width and characteristics of the mark which renders it visible.
--> The best Silhouette Score  (clusters #6): 0.49620488246084626
--> Human Eye: The silhouette score doesn't change despite the fact I changed the data variables. Is this supposed to be happening? For instance; the first image below shows the silhouette score is for the data for X = data[[ 'country_of_origin', 'representation', 'representation_semi','spatial_dimension', 'va', 'co','li']] while the second image is  X = data[[ 'representation', 'representation_semi','spatial_dimension', 'va', 'co','li']]. As you can see the silhouette scores are the same. This looks wrong. When I run the code all the way through and look at the results it looks fine. However, when I run all the code under 'final fit' again the images in the clusters change. I feel like this isn't supposed to happen since the attributes haven't been altered. Refer to image 3 and 4 to see the change of images in the cluster.

![](imgAnalysis/image1.png)
![](imgAnalysis/image2.png)
![](imgAnalysis/image3.png)
![](imgAnalysis/image4.png)

***Country_of_origin probably isn't working because it's expecting a number value. Considering the variables that have worked, which are either booleans or intergers, I think I'll need to convert country of origin to a different variable tpye. I talked to Shirley and Marisa and they said to change it to a string or numeric value. Refer to image 6. I used some code for strings sent to me by Shirley and some other code I got online --> I used ```data['country_of_origin'] = data['country_of_origin'].to_string()``` which converted the values into a numeric value somehow however I got an error for that one too. 

![](imgAnalysis/image6.png)
![](imgAnalysis/image5.png)


Iteration 3: X = data[['representation', 'representation_semi','spatial_dimension', 'va', 'co','li' ,'avgColor']]
    This iteration considers these attributes:
    representation	indicates the work represents some aspect of reality
    representation_semi	indicates the work represents some aspect of reality
    spatial_dimension	indicates the work is an object that is occupying physical space in more than 2 dimensions (height in addition to length and width)
    va	the various degrees between white and black
    co	hue, using the repertoire of colored sensations which can be produced at equal value
    li	A LINE signifies a phenomenon on the plane which has measurable length but no area. Is independent of the width and characteristics of the mark which renders it visible.
    avgColor is a sequence of numbers that indicates the 3 most common colors found in an image (my code)
--> The best Silhouette Score  (clusters #6): 0.49620488246084626
--> Human Eye: Considering that the non-boolean and integer values are not working with the system I removed those and left representation and spacial dimension in addition to avgColor which is some code I input that identifies the 3 most common colors which is represented as a sequence of numerical values. The intertia plot didn't work; I received a ```ValueError: setting an array element with a sequence.``` error. Shirley mentioned that this plot is only supposed to help with identifying the number of clusters I may need so its not necessary. Running all of the code resulted in the same issues as before, where the silhouette score is the same despite the changes to the data input. I guess that only makes sense since the code maybe ingoring the other variables that don't work and therefore only examining the integer and boolean variables which haven't changed. To confirm I will input all of the boolean and integer values in the next interation. 


Iteration 4: X = data[['has_text','representation', 'representation_semi', 'kinetic', 'map', 'map2','spatial_dimension', 'spatial_dimension2', 'pl', 'si', 'va', 'te','co', 'or','sh', 'reflection', 'po', 'li', 'ar']]
    This iteration considers these attributes: 
    representation	indicates the work represents some aspect of reality
    representation_semi	indicates the work represents some aspect of reality
    kinetic	indicates the work moves or has movement
    map	indicates the work is a map
    map2	indicates the work is a map
    spatial_dimension	indicates the work is an object that is occupying physical space in more than 2 dimensions (height in addition to length and width)
    spatial_dimension2	indicates the work is an object that is occupying physical space in more than 2 dimensions (height in addition to length and width)
    pl	given location on the planar dimensions
    si	variations in height, width, area
    va	the various degrees between white and black
    te	variation in the fineness or coarseness of an area having a given value; includes blur
    co	hue, using the repertoire of colored sensations which can be produced at equal value
    or	various orientations, ranging from the vertical to the horizontal in a distinct direction
    sh	a mark with a constant size can nonetheless have an infinite number of different shapes
    reflection	indicates the work contains an image given back by a reflecting surface, or an image seen in a mirror or shiny surface
    po	A POINT represents a location on the plane that has no theoretical length or area. This signification is independent of the size and character of the mark which renders it visible. 
    li	A LINE signifies a phenomenon on the plane which has measurable length but no area. This signification is independent of the width and characteristics of the mark which renders it visible.
    ar	An AREA signifies something on the plane that has a measurable size. This signification applies to the entire area covered by the visible mark.
--> The best Silhouette Score (clusters #6): 0.49620488246084626
--> Human Eye: Welp. Maybe the silhouette score is supposed to stay the same per cluster size. That doesn't seem right, but regardless I'm going to analyze the clustered art. The art in this cluster shows a lot of similarities in certain instances, but overall there aren't any explicit qualities that are shared among the whole from a visual stand point. As someone who really appreciates art and has a relatively thorough understanding of art history I don't believe that the qualities provided by the data here really illuminates the similarities of the pieces enough for the content within the clusters to seem assoiated. In image 7, which is apart of cluster #4, there are definitly some explicit similarities between the presented images; the smudging and frequency of lines that mimick a blurr are shared among the 3 images on the top row. However the images below do not share in the same qualities. Image 8 which is also apart of cluster #4, have two images they have repeating spheres. This association cannot be coincidental, however again we see images that are not correlated explicitly within this screenshot. In image 9, which is cluster #5, we see two images that have more subtle similarities as seen in the two greenish spheres; the marble and the plates on the wall. Image 10 and 11 compare the silhouettes and scatter plots of cluster #5 and #6. 

![](imgAnalysis/image7.png)
![](imgAnalysis/image8.png)
![](imgAnalysis/image9.png)

![](imgAnalysis/image10.png)
![](imgAnalysis/image11.png)


Iteration 5 **Last attempt considering the unchanging silhouette score** : X = data[['has_text','representation', 'representation_semi', 'kinetic', 'spatial_dimension', 'spatial_dimension2', 'pl', 'si', 'va', 'te','co', 'or','sh', 'reflection', 'ar']]
    This iteration considers these attributes: 
    has_text	indicator that the work contains text
    representation	indicates the work represents some aspect of reality
    representation_semi	indicates the work represents some aspect of reality
    kinetic	indicates the work moves or has movement
    spatial_dimension	indicates the work is an object that is occupying physical space in more than 2 dimensions (height in addition to length and width)
    spatial_dimension2	indicates the work is an object that is occupying physical space in more than 2 dimensions (height in addition to length and width)
    pl	given location on the planar dimensions
    si	variations in height, width, area
    va	the various degrees between white and black
    te	variation in the fineness or coarseness of an area having a given value; includes blur
    co	hue, using the repertoire of colored sensations which can be produced at equal value
    or	various orientations, ranging from the vertical to the horizontal in a distinct direction
    sh	a mark with a constant size can nonetheless have an infinite number of different shapes
    reflection	indicates the work contains an image given back by a reflecting surface, or an image seen in a mirror or shiny surface
    ar	An AREA signifies something on the plane that has a measurable size. This signification applies to the entire area covered by the visible mark.
--> The best Silhouette Score (clusters #5): 0.5647990853234187
--> Human Eye: In examining the silhouettes and the scatter plot. There is most definitely something wrong, as seen the in the fact that the silhouettes and splots are unchanged despite the fact the data features as been changed. I'm not sure what to do. I removed the map, po, and li features as I don't think that the data they contribute really would do a lot to change anything. 

![](imgAnalysis/image12.png)


Wanted Iteration 6: X = data[['art_movement', 'country_of_origin', 'date', 'representation', 'representation_semi','spatial_dimension', 'va', 'co','li' ,'avgColor']]
    This iteration considers these attributes:
    title	title of work
    art_movement	name of art movement
    country_of_origin	country of work
    primary_medium	broad description of medium
    date	date/year of work creation
    representation	indicates the work represents some aspect of reality
    representation_semi	indicates the work represents some aspect of reality
    spatial_dimension	indicates the work is an object that is occupying physical space in more than 2 dimensions (height in addition to length and width)
    va	the various degrees between white and black
    co	hue, using the repertoire of colored sensations which can be produced at equal value
    li	A LINE signifies a phenomenon on the plane which has measurable length but no area. Is independent of the width and characteristics of the mark which renders it visible.
    avgColor is a sequence of numbers that indicates the 3 most common colors found in an image (my code)
--> Error = ValueError: setting an array element with a sequence. [might be because of my avgColor]
--> The best Silhouette Score (clusters #5): : 0.5647990853234187
--> Human Eye: I chose these elements thinking they would be good attributes to examine on a broad scale since they have more variance while not being totally unique. Each of these elements are also relevant for 

Iteration 7 **restarted from scratch**: X = data[['pl', 'si', 'va', 'te', 'co', 'or', 'sh']]
    This iteration considers these attributes: 
    *Project default 
--> The best Silhouette Score (clusters #5): 0.18150901436135936
--> Human Eye: There are definitly some explicit similarities in some images within the clusters that are being presented however not all of them relate to one another. As seen in the previous iterations. I will start more fine tuning the features now. 

![](imgAnalysis/image13.png)

Iteration 8 **restarted from scratch**: X = data[['has_text','representation', 'representation_semi', 'kinetic', 'spatial_dimension', 'spatial_dimension2', 'pl', 'si', 'va', 'te','co', 'or','sh', 'reflection', 'ar']]

--> The best Silhouette Score (clusters #10): 0.16484964192746118
--> Human Eye: In examining the cluster0 (image 15) there are definitely more shared charactistics between each image. As seen in the picture there is a sense of depth that is illustrated through angular lines and use of cubes. Though there are some evident exceptions to that as seen in the abstract shape illustrations (image 16), but the one element that I think is pervasive of a majority images presented is a horizontal/diagonal line that may indicate depth. I find this interesting considering that I no longer have the feature 'li' which signifies a plane. I will try removing some more redunant features such as 'spatial_dimension2' as well as 'or'. 

 ![](imgAnalysis/image14.png)
 ![](imgAnalysis/image15.png)
 ![](imgAnalysis/image16.png)

Iteration 9 **restarted from scratch**: X = data[['has_text','representation', 'representation_semi', 'kinetic', 'spatial_dimension', 'pl', 'si', 'va', 'te','co','sh', 'reflection', 'ar']]

--> The best Silhouette Score (clusters #5): 0.19688918126320168
--> Human Eye: These clusters make a lot more sense despite the fact the silhouette is pretty crap (image 17). Looking at the images presented in the clusters there is an explicit color characteristic that is shared in the clusters; separating lights from dark colors. However this doesn't apply to all of the clusters presented here. Rather only 2 really fit the mark, the rest are more or less random. As seen in image 18, there is a light color chatacteristic that is shared. In image 19 it is primarily dark images. Though other than these two clusters the other 3 are random much like image 20. I will next remove 'si' and 'sh', as I think they may be to conceptual as well as too extrinsic (si -- variations in height, width, area). I may remove reflection as well since it doesn't apply to many pieces. I have a feeling the more I reduce the strong the silhouette will be.

 ![](imgAnalysis/image17.png)
 ![](imgAnalysis/image18.png)
 ![](imgAnalysis/image19.png)
 ![](imgAnalysis/image20.png)

Iteration 10 **restarted from scratch**: X = data[['has_text','representation', 'representation_semi', 'kinetic', 'spatial_dimension', 'pl', 'va', 'te','co', 'reflection', 'ar']]

--> The best Silhouette Score (clusters #5 & #7): 0.2533354022928413 & 0.25310899909714224
--> Human Eye: I went with #7 because I wanted to see how more variance would categorize the pieces. As I saw previously there is a sinlge cluster that is primarily light color pieces. The rest however do not seem to share any aesthetic characteristics. I'm thinking now I may just focus on pursely explicit visual elements like black, white, and color. To see if I can get more than 2 clusters that have similar traits. I am going to remove 'representation_semi', 'pl', and possibly 'has_text". 

 ![](imgAnalysis/image21.png)
 ![](imgAnalysis/image22.png)
 ![](imgAnalysis/image23.png)

Iteration 11 **restarted from scratch**: X = data[['has_text','representation', 'kinetic', 'spatial_dimension', 'va', 'te','co', 'reflection', 'ar']]

--> The best Silhouette Score (clusters #7): 0.3223400337005424
--> Human Eye: Considering the more features I remove the higher the silhouette score is the next round I may remove anything I deem nonessential. This sound of analysis I found that there were more clusters that had more evident shared characteristics. Starting with image 25, nearly all of the images except for a few are abstract 2 dimensional pieces in this cluster. Image 26 and 27 both shared light color qualities. Lastly, Image 28 is just an example of the random clusters that are still present. 

 ![](imgAnalysis/image24.png)
 ![](imgAnalysis/image25.png)
 ![](imgAnalysis/image26.png)
 ![](imgAnalysis/image27.png)
 ![](imgAnalysis/image28.png)

 Iteration 12 **restarted from scratch**: X = data[['representation', 'kinetic', 'spatial_dimension', 'va', 'te','co']]

--> The best Silhouette Score (clusters #7): 0.36012361679688587
--> Human Eye: Yikes. Okay so despite the increase in the silhouette score, there is no explicit correlation between any of the images within the clusters that I can tell. In the first cluster there is a ix of very dark and very light images and then the rest are just random. Image 30 will illustrate.  

 ![](imgAnalysis/image29.png)
 ![](imgAnalysis/image30.png)


Iteration 13 **restarted from scratch**: X = data[['representation', 'va', 'te', 'po', 'li', 'ar' ]]

--> The best Silhouette Score (clusters #15): 0.3119208388497599
--> Human Eye: Yikes. Okay so this is going to be my last documented one before I just start messing around with it randomly. Image 32 is the bucket of light images. Image 33 is the bucket of a majority of high contrast between variations of grey and white. As seen in almost all the images present there; if you break the image down into two main colors the primary it is a stark contrast between grey/dark and white. With the exception of a few at the bottom that are almost entirely one color. Image 34 is another bucket of light images. Image 35 is a bucket of a mix of dark and light. Again not much really connects any of these firmly. 

 ![](imgAnalysis/image31.png)
 ![](imgAnalysis/image32.png)
 ![](imgAnalysis/image33.png)
 ![](imgAnalysis/image34.png)
 ![](imgAnalysis/image35.png)


Iteration 12 **restarted from scratch**: X = data[['va', 'te', 'co', 'sh', 'po', 'li', 'ar' ]]

--> The best Silhouette Score (clusters #15): 0.3119208388497599
--> Human Eye: Yikes. Okay so this is going to be my last documented one before I just start messing around with it randomly. Image 32 is the bucket of light images. Image 33 is the bucket of a majority of high contrast between variations of grey and white. As seen in almost all the images present there; if you break the image down into two main colors the primary it is a stark contrast between grey/dark and white. With the exception of a few at the bottom that are almost entirely one color. Image 34 is another bucket of light images. Image 35 is a bucket of a mix of dark and light. Again not much really connects any of these firmly. 

Iteration 13 **restarted from scratch**: X = data[['te', 'co','or', 'li']]

--> The best Silhouette Score (clusters #22): 0.4009184054753453
--> Human Eye: This was the highest silhouette score I could manage with the given data. Image 40 is the silhouette illusrration. Image 36 is cluster 0 and features a variety of images that seem to share a similar blurr or fizzed effect. Image 37 is cluster 6 and features a variety of images that seem to share a characteristic related to the repetition of lines. Cluster 19 and 20, is in image 38. Cluster 19 features a variety of soft curves while cluster 20 features an emphasis on horizontal lines. Lastly image 39 which features both cluster 2 and 3 illustrates a variety of colored images with beige-like backgrounds while the latter is connected by single objects juxtaposed in the center of the composition. 

 ![](imgAnalysis/image40.png)
 ![](imgAnalysis/image36.png)
 ![](imgAnalysis/image37.png)
 ![](imgAnalysis/image38.png)
 ![](imgAnalysis/image39.png)