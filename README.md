import java.util.ArrayList;
import java.util.Scanner;

class Product {
    private String name;
    private double price;
    private int quantity;

    public Product(String name, double price, int quantity) {
        this.name = name;
        this.price = price;
        this.quantity = quantity;
    }

    public String getName() {
        return name;
    }

    public double getPrice() {
        return price;
    }

    public int getQuantity() {
        return quantity;
    }

    @Override
    public String toString() {
        return "Product{name='" + name + "', price=" + price + ", quantity=" + quantity + "}";
    }
}

public class InventoryManagement {
    private static ArrayList<Product> inventory = new ArrayList<>();

    public static void addProduct(String name, double price, int quantity) {
        Product product = new Product(name, price, quantity);
        inventory.add(product);
        System.out.println("Product added successfully!");
    }

    public static void viewInventory() {
        System.out.println("Inventory:");
        for (Product product : inventory) {
            System.out.println(product);
        }
    }

    public static void searchProduct(String name) {
        boolean found = false;
        for (Product product : inventory) {
            if (product.getName().equalsIgnoreCase(name)) {
                System.out.println(product);
                found = true;
            }
        }
        if (!found) {
            System.out.println("Product not found.");
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int choice;
        do {
            System.out.println("1. Add Product");
            System.out.println("2. View Inventory");
            System.out.println("3. Search Product");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            scanner.nextLine();  // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter product name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter product price: ");
                    double price = scanner.nextDouble();
                    System.out.print("Enter product quantity: ");
                    int quantity = scanner.nextInt();
                    addProduct(name, price, quantity);
                    break;
                case 2:
                    viewInventory();
                    break;
                case 3:
                    System.out.print("Enter product name to search: ");
                    String searchName = scanner.nextLine();
                    searchProduct(searchName);
                    break;
                case 4:
                    System.out.println("Exiting...");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        } while (choice != 4);

        scanner.close();
    }
}
