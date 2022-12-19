package week10;

/**
 *
 * @author yaser
 */
public interface ToBeStored {
    double weight();
}

/**
 *
 * @author yaser
 */
public interface NationalService {
    int getDaysLeft();
    void work();
}
/**
 *
 * @author yaser
 */
public class GenericClass<T> {
    private T value; 
    
    public GenericClass(T v){
        this.value = v;
    }
    
    public T getValue(){
        return this.value;
    }
    
}

 * @author yaser
 */
public class CivilService implements NationalService{

    private int daysLeft; 
    
    public CivilService(){
        this.daysLeft = 362;
    }

    @Override
    public int getDaysLeft() {
        return this.daysLeft;
    }

    @Override
    public void work() {
        if(this.daysLeft > 0){
            this.daysLeft--;
        }
    }
  * @author yaser
 */
public class MilitaryService implements NationalService{

    private int daysLeft; 
    
    public MilitaryService(int daysLeft){
        this.daysLeft = daysLeft;
    }
    
    @Override
    public int getDaysLeft() {
        return this.daysLeft;
    }

    @Override
    public void work() {
        if(this.daysLeft > 0){
            this.daysLeft--;
        }
    }
    /**
 *
 * @author yaser
 */
public class Book implements ToBeStored {
    private String writer;
    private String name; 
    private double weight; 
    
    public Book(String wr, String n, double w){
        this.writer = wr;
        this.name = n; 
        this.weight = w;
    }
    
    @Override
    public double weight() {
        return this.weight;
    }
    
    public String toString(){
        return this.writer + ": " + this.name;
    }
    
}
/**
 *
 * @author yaser
 */
public class Purchase {
    private String product;
    private int amount; 
    private int unitPrice;
    
    public Purchase(String p, int a, int uP){
        this.product = p;
        this.amount = a;
        this.unitPrice = uP;
    }
    
    public int price(){
        return this.amount * this.unitPrice;
    }
    
    public void increaseAmount(){
        this.amount++; 
    }
    
    public String toString(){
        return this.product + ": " + this.amount;
    }
    
    
    
}

* @author yaser
 */
public class CD implements ToBeStored{
    private String artist;
    private String title; 
    private int publishingYear;
    private double weight; 
    
    public CD(String a, String t, int pY){
        this.artist = a;
        this.title = t; 
        this.publishingYear = pY;
        this.weight = 0.1;
    }
    
    @Override
    public double weight() {
      return this.weight;
    }
    
    public String toString(){
        return this.artist + ": " + this.title + " (" + this.publishingYear + ")";
    }
}

/**
 *
 * @author yaser
 */
public class Box {
    private double maxWeight;
    private double currentWeight;
    private int numberOfThings;
    
    public Box(double maxWeight) {
        this.maxWeight = maxWeight;
        this.currentWeight = 0;
        this.numberOfThings = 0;
    }
    
    public void add(ToBeStored object) {
        if((this.currentWeight + object.weight()) <= this.maxWeight) {
            this.currentWeight += object.weight();
            this.numberOfThings++;
        }
    }
    
    public String toString(){
        return "Box: " + numberOfThings + " things, total weight " + this.currentWeight + " kg";
    }
}

import java.util.HashMap;
import java.util.Map;

/**
 *
 * @author yaser
 */
public class ShoppingBasket {
    Map<String, Purchase> basket; 
    
    public ShoppingBasket(){
        basket = new HashMap<String, Purchase>();
    }
    
    public void add(String product, int price){ 
        if(basket.containsKey(product)){
            basket.get(product).increaseAmount();
        }else {
             Purchase purchase = new Purchase(product, 1, price);
             basket.put(product, purchase);
        }
    }
    
    public int price(){
        int total_price = 0;
        
        for(Purchase p : basket.values()){
            total_price = total_price + p.price();
        }
        
        return total_price;        
    }
    
    public void print(){
        for(Purchase p : basket.values()){
            System.out.println(p);
        }
    }
    
    import java.util.HashMap;
import java.util.Map;
import java.util.Set;

/**
 *
 * @author yaser
 */
public class Storehouse {
    Map<String, Integer> prices;
    Map<String, Integer> stocks; 
    
    public Storehouse(){
        this.prices = new HashMap<String, Integer>();
        this.stocks = new HashMap<String, Integer>();
    }
    
    public void addProduct(String product, int price, int stock){
          prices.put(product, price);
          stocks.put(product, stock);
    }
    
    public int price(String product){
        if(prices.containsKey(product)){
            return prices.get(product);
        }else{
            return -99;
        }
    }
    
    public int stock(String product){
        if(stocks.containsKey(product)){
            return stocks.get(product);
        }else{
            return 0;
        }
    }
    
    public boolean take(String product){
        if(stocks.containsKey(product)){
            if(stocks.get(product) > 0){
                stocks.put(product, stocks.get(product)-1);
                return true;
            }else{
                return false;
            }
        }else{
            return false;
        }
    }
    
    public Set<String> products(){
        return prices.keySet();
    }
    
    
}
* @author yaser
 */
public class Shop {
    private Storehouse store;
    private Scanner reader;

    public Shop(Storehouse store, Scanner reader) {
        this.store = store;
        this.reader = reader;
    }

    // the method to deal with a customer in the shop
    public void manage(String customer) {
        ShoppingBasket basket = new ShoppingBasket();
        System.out.println("Welcome to our shop " + customer);
        System.out.println("below is our sale offer:");

        for (String product : store.products()) {
            System.out.println( product );
        }

        while (true) {
            System.out.print("what do you want to buy (press enter to pay):");
            String product = reader.nextLine();
            if (product.isEmpty()) {
                break;
            }
            
            if(store.stock(product) > 0){
                store.take(product);
                basket.add(product, store.price(product));
            }

            // here, you write the code to add a product to the shopping basket, if the storehouse is not empty
            // and decreases the storehouse stocks
            // do not touch the rest of the code!

        }

        System.out.println("your purchases are:");
        basket.print();
        System.out.println("basket price: " + basket.price());
    }
}
import java.util.Scanner;

/**
 *
 * @author yaser
 */
public class Week10 {

    /**
    
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        /*Book book1 = new Book("Fedor Dostojevski", "Crime and Punishment", 2);
        Book book2 = new Book("Robert Martin", "Clean Code", 1);
        Book book3 = new Book("Kent Beck", "Test Driven Development", 0.5);

        CD cd1 = new CD("Pink Floyd", "Dark Side of the Moon", 1973);
        CD cd2 = new CD("Wigwam", "Nuclear Nightclub", 1975);
        CD cd3 = new CD("Rendezvous Park", "Closer to Being Here", 2012);

        System.out.println(book1);
        System.out.println(book2);
        System.out.println(book3);
        System.out.println(cd1);
        System.out.println(cd2);
        System.out.println(cd3);*/
      
        /*Box box = new Box(10);

        box.add( new Book("Fedor Dostojevski", "Crime and Punishment", 2) ) ;
        box.add( new Book("Robert Martin", "Clean Code", 1) );
        box.add( new Book("Kent Beck", "Test Driven Development", 0.7) );

        box.add( new CD("Pink Floyd", "Dark Side of the Moon", 1973) );
        box.add( new CD("Wigwam", "Nuclear Nightclub", 1975) );
        box.add( new CD("Rendezvous Park", "Closer to Being Here", 2012) );

        System.out.println( box );*/
       
       /*GenericClass<Integer> g1 = new GenericClass(10);
       System.out.println("Integer: " + g1.getValue());
       GenericClass<String> g2 = new GenericClass("Hello");
       System.out.println("String: " + g2.getValue());*/
       
        /*Storehouse store = new Storehouse();
        store.addProduct("milk", 3, 10);
        store.addProduct("coffee", 5, 7);

        System.out.println("prices:");
        System.out.println("milk:  " + store.price("milk"));
        System.out.println("coffee:  " + store.price("coffee"));
        System.out.println("sugar: " + store.price("sugar"));*/
        
        /*Storehouse store = new Storehouse();
        store.addProduct("coffee", 5, 1);

        System.out.println("stocks:");
        System.out.println("coffee:  " + store.stock("coffee"));
        System.out.println("sugar: " + store.stock("sugar"));

        System.out.println("we take a coffee " + store.take("coffee"));
        System.out.println("we take a coffee " + store.take("coffee"));
        System.out.println("we take sugar " + store.take("sugar"));

        System.out.println("stocks:");
        System.out.println("coffee:  " + store.stock("coffee"));
        System.out.println("sugar: " + store.stock("sugar"));*/
       
       
        /*Storehouse store = new Storehouse();
        store.addProduct("milk", 3, 10);
        store.addProduct("coffee", 5, 6);
        store.addProduct("buttermilk", 2, 20);
        store.addProduct("jogurt", 2, 20);

        System.out.println("products:");
        for (String product : store.products()) {
            System.out.println(product);
        }*/
        
        /*Purchase purchase = new Purchase("milk", 4, 2);
        System.out.println( "the total price of a purchase containing four milks is " + purchase.price() );
        System.out.println( purchase );
        purchase.increaseAmount();
        System.out.println( purchase );*/
     
        /*ShoppingBasket basket = new ShoppingBasket();
        basket.add("milk", 3);
        basket.add("buttermilk", 2);
        basket.add("cheese", 5);
        System.out.println("basket price: " + basket.price());
        basket.add("computer", 899);
        System.out.println("basket price: " + basket.price());
        
        basket.print();*/
        
        /*ShoppingBasket basket = new ShoppingBasket();
        basket.add("milk", 3);
        basket.print();
        System.out.println("basket price: " + basket.price() +"\n");

        basket.add("buttermilk", 2);
        basket.print();
        System.out.println("basket price: " + basket.price() +"\n");

        basket.add("milk", 3);
        basket.print();
        System.out.println("basket price: " + basket.price() +"\n");

        basket.add("milk", 3);
        basket.print();
        System.out.println("basket price: " + basket.price() +"\n");*/
            
        Storehouse store = new Storehouse();
        store.addProduct("coffee", 5, 10);
        store.addProduct("milk", 3, 20);
        store.addProduct("milkbutter", 2, 55);
        store.addProduct("bread", 7, 8);

        Shop shop = new Shop(store, new Scanner(System.in));
        shop.manage("Pekka");
    }
    
}



  


