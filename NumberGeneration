import java.util.Arrays;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;

class Order {
    private String product;
    private double cost;

    public Order(String product, double cost) {
        this.product = product;
        this.cost = cost;
    }

    public String getProduct() { return product; }
    public double getCost() { return cost; }
}

public class NumberGeneration {
    public static void main(String[] args) {

        List<Order> orders = Arrays.asList(
            new Order("laptop", 1200.0),
            new Order("smartphone", 800.0),
            new Order("laptop", 1500.0),
            new Order("tablet", 500.0),
            new Order("smartphone", 900.0)
        );

        // Step 1: group and sum
        Map<String, Double> totals = orders.stream()
            .collect(Collectors.groupingBy(
                Order::getProduct,
                Collectors.summingDouble(Order::getCost)
            ));

        // Step 2: sort and take top 3
        List<Map.Entry<String, Double>> top3 = totals.entrySet().stream()
            .sorted(Map.Entry.<String, Double>comparingByValue().reversed())
            .limit(3)
            .collect(Collectors.toList());

        // Step 3: print
        for (Map.Entry<String, Double> entry : top3) {
            System.out.println(entry.getKey() + " → $" + entry.getValue());
        }
    }
}
