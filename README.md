# consultaGoogleBooks
https://copilot.microsoft.com/shares/oSB27H8sYGHZR3YLpebfu



/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Main.java to edit this template
 */
package googlebookssearch;

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;
/**
 *
 * @author SEEMG
 */
public class GoogleBooksSearch {
 
    private static final String BASE_URL = "https://www.googleapis.com/books/v1/volumes";

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
          String query = "Romeo";
        String result = searchBooks(query);
        System.out.println(result);
        
    }
      public static String searchBooks(String query) {
        String urlString = BASE_URL + "?q=" + query;
        try {
            URL url = new URL(urlString);
            HttpURLConnection connection = (HttpURLConnection) url.openConnection();
            connection.setRequestMethod("GET");

            BufferedReader reader = new BufferedReader(new InputStreamReader(connection.getInputStream()));
            StringBuilder json = new StringBuilder();
            String line;
            while ((line = reader.readLine()) != null) {
                json.append(line);
            }
            reader.close();

            return json.toString();
        } catch (Exception e) {
            e.printStackTrace();
            return null;
        }
    }
}
    


