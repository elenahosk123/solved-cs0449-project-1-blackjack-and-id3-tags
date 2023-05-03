Download Link: https://assignmentchef.com/product/solved-cs0449-project-1-blackjack-and-id3-tags
<br>
Your first project is to write two programs in C that provide some experience with a wide range of the topics we have been discussing in class.

<strong>Blackjack Implementation </strong>

Blackjack (also known as 21) is a multiplayer card game, with fairly simple rules. For this assignment, you will be implementing a simplified version where a user can play against the computer who acts as dealer.

Two cards are dealt to each player. The dealer shows one card face up, and the other is face down.  The player gets to see both of his or her cards and the total of them is added. Face cards (Kings, Queens, and Jacks) are worth 10 points, Aces are worth 1 or 11 points, and all other cards are worth their face value. The goal of the game is to get as close to 21 (“blackjack”) without going over (called “busting”).

The human player goes first, making his or her decisions based on the single dealer card showing. The player has two choices: Hit or Stand. Hit means to take another card. Stand means that the player wishes no more cards, and ends the turn, allowing for the dealer to play.

The dealer must hit if their card total is less than 17, and must stand if it is 17 or higher.

Whichever player gets closest to 21 without exceeding it, wins.




The dealer:

? + 10




You:

4 + 10 = 14

Would you like to “hit” or “stand”? hit

The dealer:

? + 10




You:

14 + 10 = 24 BUSTED!




You busted. Dealer wins.

<strong> </strong>

<strong>Requirements and Hints </strong>

<ul>

 <li>Have the program intelligently determine if an Ace should be interpreted as a 1 or an 11 by counting the number of aces dealt and adjusting the total down if over 21 and an ace exists.</li>

 <li>Generating random numbers in C is a two-step part. First, we need to seed the random number generator <em>once</em> per program. The idiom to do this is:srand((unsigned int)time(NULL));</li>

 <li>When we need random numbers, we can use the rand() function. It returns an unsigned integer between 0 and RAND_MAX. We can use modulus to reduce it to the range we need:int value = rand() % (high – low + 1) + low;</li>

 <li>Remember that getting a card worth 10 is more common because of the face cards, so generate a random card, not a random value.</li>

</ul>

<strong>ID3 Tag Editor (70 points)</strong>

An ID3 version 1.1 tag for MP3s (and other multimedia files) adds metadata describing the file. The contents of an ID3 tag are the following:

<table>

 <tbody>

  <tr>

   <td width="119"><strong>Offset</strong></td>

   <td width="92"><strong>length</strong></td>

   <td width="247"><strong>description</strong></td>

  </tr>

  <tr>

   <td width="119">0</td>

   <td width="92">3</td>

   <td width="247">“TAG” identifier string.</td>

  </tr>

  <tr>

   <td width="119">3</td>

   <td width="92">30</td>

   <td width="247">Song title string.</td>

  </tr>

  <tr>

   <td width="119">33</td>

   <td width="92">30</td>

   <td width="247">Artist string.</td>

  </tr>

  <tr>

   <td width="119">63</td>

   <td width="92">30</td>

   <td width="247">Album string.</td>

  </tr>

  <tr>

   <td width="119">93</td>

   <td width="92">4</td>

   <td width="247">Year string.</td>

  </tr>

  <tr>

   <td width="119">97</td>

   <td width="92">28</td>

   <td width="247">Comment string.</td>

  </tr>

  <tr>

   <td width="119">125</td>

   <td width="92">1</td>

   <td width="247">Zero byte separator.</td>

  </tr>

  <tr>

   <td width="119">126</td>

   <td width="92">1</td>

   <td width="247">Track number byte.</td>

  </tr>

  <tr>

   <td width="119">127</td>

   <td width="92">1</td>

   <td width="247">Genre identifier byte.</td>

  </tr>

 </tbody>

</table>




An ID3 (v1.1) tag like above is appended to a file as the last 128 bytes. The tag is present if at the -128 from end offset there are the three ASCII characters TAG.

<strong>What to Do</strong>

For your project you will make a utility that can print the contents of an existing tag, if there, and add or modify a tag.

Make a program called id3tagEd and make it so that it runs with the following command line options:

id3tagEd FILENAME

should print the contents of the ID3 tag to the console if present, or give a message if not present

id3tagEd FILENAME -FIELD VALUE

should set the specified field to the value that follows it. You should handle the following field names (specified in lowercase):

<ul>

 <li>Title</li>

 <li>Artist</li>

 <li>Album</li>

 <li>Year</li>

 <li>Comment</li>

 <li>Track</li>

</ul>




Make sure you are able to handle multiple {field, value} pairs on the command line at once. If the tag already exists in the specified file, then edit it, if not create a new tag by appending a tag at the end with the specified fields populated. Assume all others are to be empty (filled with 0s.)

<strong>Hints and Requirements</strong>

<ul>

 <li>The strings may not have a null-terminator. Be careful that you do the right thing in these cases. Look into the strn family of functions.</li>

 <li>We need to treat these files as <em>binary files</em> rather than <em>text files</em>. Make sure to open the file correctly, and to use fread and fwrite for I/O.</li>

 <li>Please use a structure to represent an ID3 tag rather than a bunch of disjoint strings. Do your fread() and fwrite() with the whole structure at once. (That is, read or write an entire tag in one file operation.)</li>

 <li>Note that you do NOT need to handle the genre field. Just leave it unchanged if editing, and make it 0 if making a new tag.</li>

 <li>atoi() from &lt;stdlib.h&gt; converts a string to an integer in the fashion of Integer.parseInt()</li>

</ul>

<strong>Environment</strong>

Ensure that your program builds and runs on thoth.cs.pitt.edu as that will be where we are testing.