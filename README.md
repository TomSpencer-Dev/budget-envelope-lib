# Budget Envelope $ Investment Library (v1.0.0)

A Java library used as a backend engine. It is designed to set budget 
allocations into envelopes based on percentage. It can also calculate the 
long-term compounded growth on an investment account.

## Library Components
1. **Envelopes.java**: A data container that stores final calculated envelope balances.
2. **EnvelopesEngine.java**: The mathematical engine that splits income into custom categories.
3. **InvestmentEngine.java**: An engine that compounds interest year by year to show the potential growth of investments.

## Add library to existing Java project
1.	Navigate to https://github.com/TomSpencer-Dev/budget-envelope-lib/releases/tag/V1.0.0.
2.	Click the budget-envelope-lib-1.0-SNAPSHOT.jar file to download it.
3.	Create a new Java Project.
4.	Create a folder named libs inside your new Java project.
5.	Drag and drop the JAR file into that folder.
6.	Right-click the JAR file inside your IDE and select Add as Library (or Add to Build Path).

## Usage Instructions

To implement this library, import the package and execute the engine

```java
// import the budget-envelope library along with HashMap and Map libraries
import org.budget.envelope.*;
import java.util.HashMap;
import java.util.Map;

//Initialize a Map of envelopes as a HashMap with envelope name and percentage of overall budget
Map<String, Double> envelopes = new HashMap<>();
envelopes.put("Necessitites", 0.50);
envelopes.put("Spending", 0.30);
envelopes.put("Investments", 0.20);

// Create a payment received amount
EnvelopesEngine engine = new EnvelopesEngine();
Envelopes payReceived = engine.allocateFunds(4000.00, envelopes);

//Project investment growth over 10 years at 7% interest rate
InvestmentEngine investmentEngine = new InvestmentEngine();
double investmentBalance = payReceived.getBalance("Investments");
Map<Integer, Double> schedule = investmentEngine.calculateGrowthSchedule(investmentBalance, 0.07, 10);
```
