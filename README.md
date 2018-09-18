package LAB2;

import java.io.File;
import javax.xml.parsers.DocumentBuilderFactory;
import javax.xml.parsers.DocumentBuilder;
import org.w3c.dom.Document;
import org.w3c.dom.NodeList;
import org.w3c.dom.Node;
import org.w3c.dom.Element;

public class Main {

   public static void main(String[] args) {

      try {
         File inputFile = new File("places.xml");
         DocumentBuilderFactory dbFactory = DocumentBuilderFactory.newInstance();
         DocumentBuilder dBuilder = dbFactory.newDocumentBuilder();
         Document doc = dBuilder.parse(inputFile);
         doc.getDocumentElement().normalize();
         System.out.println("Root element : " + doc.getDocumentElement().getNodeName());
         NodeList nList = doc.getElementsByTagName("locality");
         NodeList vList = doc.getElementsByTagName("location");
         System.out.println("----------------------------");
         
         for (int temp = 0; temp < nList.getLength(); temp++) {
             Node nNode = nList.item(temp);
             Node vNode = vList.item(temp);
             System.out.println("\nCurrent Element : " + nNode.getNodeName());
         
         
             if (nNode.getNodeType() == Node.ELEMENT_NODE) {
            	 Element eElement = (Element) nNode;
            	 Element vElement = (Element) vNode;
            	 System.out.println("Location : " 
            			 + eElement.getAttribute("name"));
            	 		
            	 System.out.println("altitude : " 
            			 + vElement.getAttribute("altitude"));
            	System.out.println("latitude : "
            			 + vElement.getAttribute("latitude"));
            	System.out.println("longitude : "
           			 + vElement.getAttribute("longitude"));
            	 		
            			
            	
             }
         }
         
      } catch (Exception e) {
          e.printStackTrace();
      }
      
   }
}
