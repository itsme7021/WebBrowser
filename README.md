# WebBrowser
Web Browser made using javafx

The idea is to make a web browser using the methods present in javafx.
We know that javafx has much more functions than java swing
We made basic functions with java swing and the panel using javafx and the other things are handled by webView.

#CODE

import javafx.application.Platform;
import javafx.embed.swing.JFXPanel;
import javafx.scene.Scene;
import javafx.scene.web.WebView;

import javax.swing.*;

//we are gonna implement runnable instead of extending the thread class
// coz java doesnt allow multi inheritance
public class main extends JFrame implements Runnable{
    //we are gonna use javafx in this bcoz we use javafx for creating
    //gui and dynamic windows and it has features that swing doesnt have
    private JFXPanel pan;
    public void run()
    {
        this.setBounds(0,0,1920 , 1080); //setBounds is a combination of setlocation and setsize function , first two aguements location
                            //other two are size
        this.setTitle("Ayush's Browser");
        this.setDefaultCloseOperation(EXIT_ON_CLOSE);
        this.setVisible(true);

        pan = new JFXPanel();
        add(pan);

        //plattform uses arrow function which is introduced in java8 only
        // and as we have to tell our function which part to run later thus we use this

        Platform.runLater(() -> {

            //webView manages all the search engine on its own and displays the contents of it and they cant be changed(the content)
            WebView we = new WebView();
            we.getEngine().load("https://www.google.com/"); //this command gives us the engine & to open a website by default we use the load method

            //unlike swing we dont have to use add function directly to add something to the panel
            //in javafx use the scene class to add something to the panel

            pan.setScene(new Scene(we));
        });



    }

    public static void main(String[] args) {
        // as some methods of swing class are not thread safe thus we use this invoke later function that invokes the
        //the methods later
        SwingUtilities.invokeLater(new main());

        // Steps to make a jar file in intellij idea
        //Steps are:
        //1. go to project structure -> artifacts
        // 2. go to the + in the upper bar -> jar -> modules with dependencies
        // 3. in the main class tab select the main class and then ok
        // 4. then go to build tab in the upper bar -> Build artifacts -> build jar
        // 5. go look for your jar file in te out -> artifacts -> project name
        // 6. copy the location by right clicking on it.

    }

}
