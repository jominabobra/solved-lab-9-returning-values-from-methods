Download Link: https://assignmentchef.com/product/solved-lab-9-returning-values-from-methods
<br>
<strong><em>Objectives:</em> </strong>

<ol>

 <li>To understand how methods return values</li>

 <li>To use method return values</li>

</ol>

<strong><em>Preparation:</em> </strong>

<ol>

 <li>Go over the Lecture Notes: Topic 11.</li>

 <li>Textbook Reading (optional): Chapter 5 section 5.2.5, 5.3.3</li>

</ol>

<h1>Exercise 1:  Writing a Picture method that returns an integer</h1>

<ol>

 <li>a) In Topic 11 of the Lecture Notes we saw a method for the Picture class called countWhitePixels() that returns the number of white pixels in a picture. This method is provided below. Using this method as a model, write a new method called countNonWhitePixels() that returns the number of pixels in a picture that are <strong>not</strong> Change <strong>only</strong> the method name and the if statement.</li>

</ol>




public int countWhitePixels()

{

Pixel pixelObj;    int counter = 0;

// loop through the columns (x direction)       for (int x = 0; x &lt; this.getWidth(); x++)

{

// loop through the rows (y direction)

for (int y = 0; y &lt; this.getHeight(); y++)

{

// get the pixel at the x and y location           pixelObj = this.getPixel(x,y);




if (pixelObj.getRed()==255 &amp;&amp; pixelObj.getGreen()==255

&amp;&amp; pixelObj.getBlue()== 255)               counter = counter + 1;

}        }

return counter;

}




<ol>

 <li>Test your new method in the Interactions pane on <em>jpg.</em> To see if you are getting the correct count returned, first call countWhitePixels()to see how many pixels are white. Then call your new method countNonWhitePixels(). What should be the value that it returns? (Hint: How many pixels are there in total for this picture?)</li>

</ol>




<ol>

 <li>There is another way to approach the writing of the countNonWhitePixels() method, using the countWhitePixels() method that already exists. We can call a method that is in the Picture class from within another method that is in the Picture class (we have been doing this with getWidth() and getHeight() already, just as we do in the provided code below). So, fill in the blanks in the method countNonWhitePixels2() provided below to get the same result as in part a)</li>

</ol>




public int countNonWhitePixels2()

{

int numPixels = this.getHeight()* this.getWidth();




int numNotWhite = numPixels –  __________________;




return numNotWhite;

}




<ol>

 <li>Test your new method in the Interactions pane on <em>jpg</em></li>

</ol>




<ol>

 <li>Optional: Rewrite the method countNonWhitePixels2() so that the body of the method consists of only one statement. (Hint: the return keyword can be followed by an expression.)</li>

</ol>

<strong>  </strong>

<strong>  </strong>

<h1>Exercise 2: Writing a Picture method that returns a boolean value</h1>

<strong> </strong>

All of the <em>conditions</em> that we have seen in while loops and for loops and if statements are Boolean (logical) expressions, i.e. they evaluate to either true or false. In this exercise, you will write a method that returns true or false. What will be the return type of the method?

<ol>

 <li>Create a new method in the Picture class that compares the size of two pictures.</li>

</ol>

The method will be called equalPictureSize and will take one parameter that is a Picture object. It will have the header (you fill in the return type):

public ___ equalPictureSize (Picture otherPicture) <strong> </strong>

This method will be invoked on a Picture object. If this picture has the same width and height as the picture referenced by the parameter variable otherPicture, the method returns true, otherwise it returns false.

<strong> </strong>

<ol>

 <li>Test your new method in the Interactions pane by using two pictures that are the same size (for example <em>jpg</em> and <em>flower2.jpg</em>) and then two pictures that you know are of different height and width (for example <em>caterpillar.jpg</em> and <em>flower1.jpg</em>).</li>

</ol>

<h1>Exercise 3: Writing a Picture method that returns a Picture object</h1>

Provided below is the code for the Picture method copyPicture() from Topic 9 page 10. Recall that it is invoked on the target picture, and copies the source picture to the top left corner of the target picture.

<ol>

 <li>First, you will write a new method for the Picture class called copyLeftHalf() that functions exactly like copyPicture(), but only copies the <strong>left half</strong> of the</li>

</ol>

source picture to the target picture. It will have the header

public void copyLeftHalf(Picture sourcePicture)

(Hint: all you need to change in the body of the method is the limit on the sourceX coordinate!)







<ol start="480">

 <li>Test your new method with the image in <em>jpg</em> as the source picture, and <em>640×480.jpg</em> as the target picture. Why is there white space around the halfcaterpillar picture?</li>

</ol>







<ol>

 <li>Now suppose we wanted the target picture to be just the left half of the source picture, with <strong>no</strong> white space around it. In other words, we want our target picture to be of a size that <em>depends on the size of the source picture</em>. We discussed this idea in Topic 11 of the lecture notes: why and how to return a Picture object from a method. Write a different version of the method copyLeftHalf() of part a) so that it has the header:</li>

</ol>




public Picture copyLeftHalf()




that will be <strong>invoked on the source picture</strong>, and that will <strong>return the target picture</strong>.




(Hint: See how the copyLeftRotation() method in Topic 11 is changed from the version that has a header similar to your method of part a), to the version that has a header similar to the method you now want. Note that this includes adding code to your new version to create a new target picture that will be just the

left half of the source picture. What should be the size of the new target picture?) (Note that your new version of copyLeftHalf() has the same method name as your original copyLeftHalf() method. Why is this not a problem for the Java compiler?)










<ol>

 <li>d) Test your new method using the following statements in the Interactions pane, choosing the file <em>jpg</em> as before.</li>

</ol>




Picture sourcePic = new Picture(FileChooser.pickAFile());

Picture targetPic =  sourcePic.copyLeftHalf(); targetPic.explore();

public void copyPicture (Picture sourcePicture)

{

Pixel sourcePixel = null;

Pixel targetPixel = null;

// loop through the columns    for (int sourceX = 0, targetX = 0;         sourceX &lt; sourcePicture.getWidth();

sourceX++, targetX++)

{

// loop through the rows      for (int sourceY = 0, targetY = 0;           sourceY &lt; sourcePicture.getHeight();

sourceY++, targetY++)

{




// set the target pixel color to the source pixel color        sourcePixel = sourcePicture.getPixel(sourceX,sourceY);        targetPixel = this.getPixel(targetX,targetY);        targetPixel.setColor(sourcePixel.getColor());

}

}

}








