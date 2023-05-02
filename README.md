Download Link: https://assignmentchef.com/product/solved-cnt5106-computer-networks-project-2
<br>
<h1>Implementation of P2P network</h1>




This project is a team project and each team consists of <strong>one or two</strong> students. The goal is to create a peer-to-peer network for file downloading. It resembles some features of Bittorrent, but much simplified. There are two pieces of software – <strong><em>peer</em></strong> and <strong><em>file owner</em></strong>.




The <strong>file owner</strong> has a file, and it breaks the file into chunks of 100KB, each stored as a separate file. Note that the last chunk can be smaller than 100KB. The <strong>minimum</strong> number of chunks that the file can be split into is 5. The file owner listens on a TCP port. It should be designed as a server that can run multiple threads to serve multiple clients simultaneously.




Each <strong>peer</strong> should be able to connect to the file owner to download some chunks. It then should have two threads of control, one acting as a server that uploads the local chunks to another peer (referred to as <em>upload neighbor</em>), and the other acting as a client that downloads chunks from a third peer (referred to as <em>download neighbor</em>). So each peer has two neighbors, one of which will get chunks from this peer and the other will send chunks to this peer. You can arbitrarily decide on the neighboring relationship as long as the network is connected — there is a direct path from any peer to any other peer. The neighboring relationship may be encoded through input parameters (see below).




<ol>

 <li>Start the file owner process, giving a listening port.</li>

 <li>Start five peer processes, one at a time, giving the file owner’s listening port, the peer’s listening port, and its download neighbor’s (another peer) listening port.</li>

 <li>Each peer connects to the server’s listening port. The latter creates a new thread to upload one or several file chunks to the peer, while its main thread goes back to listening for new peers.</li>

 <li>After receiving chunk(s) from the file owner, the peer stores them as separate file(s) and creates a summary file, listing the IDs of the chunks it has.</li>

 <li>The peer then proceeds with two new threads, with one thread listening to its upload neighbor to which it will upload file chunks, and the other thread connecting to its download neighbor.</li>

 <li>The peer requests for the chunk ID list from the download neighbor, compares with its own to find the missing ones, and randomly requests a missing chunk from the neighbor. In the meantime, it sends its own chunk ID list to its upload neighbor, and upon request uploads chunks to the neighbor.</li>

 <li>After a peer has all file chunks, it combines them for a single file.</li>

 <li>A peer MUST output its activity to its console <strong>whenever</strong> it receives a chunk, sends a chunk, receives a chunk ID list, sends out a chunk ID list, requests for chunks, or receives such a request.</li>

</ol>







<h1>Other Information</h1>

<strong>Programming Environment </strong>

Programming language:  Java, C, C++, C#, Python Operating System: Windows, Mac OS or Linux

Programming Tool: Eclipse, IntelliJ, Jcreator, Netbeans, … whatever you like.




To use Eclipse, please go through the following list:

<ol>

 <li>Download JDK from:</li>

</ol>

<a href="https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html">https://www.oracle.com/technetwork/java/javase/downloads/jdk8</a><a href="https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html">–</a><a href="https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html">downloads</a><a href="https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html">2133151.html</a>

<ol start="2">

 <li>Download Eclipse from: <a href="https://www.eclipse.org/downloads/">http://www.eclipse.org/downloads/</a> Here is a link for eclipse tutorial: <a href="http://eclipsetutorial.sourceforge.net/totalbeginner.html">http://eclipsetutorial.sourceforge.net/totalbeginner.html</a></li>

 <li>Here is a tutorial for socket programming in Java: <a href="http://java.sun.com/docs/books/tutorial/networking/sockets/">http://java.sun.com/docs/books/tutorial/networking/sockets/</a></li>

</ol>




<strong>Demo Policy: </strong>

<h2>1. Before Demo</h2>

<ul>

 <li>Each group of student(s) must sign up a time.</li>

 <li>A sign-in sheet will be posted on Canvas before demo. You can pick an idle time slot and put down <strong>ALL</strong> team members’ names and UFIDs.</li>

 <li>Please do not replace another group’s information in a time slot and you must show up during the time slot that you sign up for.</li>

</ul>

<h2>2. During Demo</h2>

<ul>

 <li>10 minutes presentation.</li>

 <li>Whole team must be present and demo your project during December 5, 6 at E309/E312.</li>

 <li>You can use a CISE computer or your laptop for the demo.</li>

 <li>We will use the source code you <strong>uploaded</strong> on Canvas and a file named test.pdf of more than 5 chunks to test your code.</li>

 <li>Run file owner and peers, and explain your code.</li>

 <li><strong>Minimum</strong> Expectation from the program:</li>

</ul>

1) All log information on the activities of the file owner and five peers; 2) The file is fully recovered in all peers.