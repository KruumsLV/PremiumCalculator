# Policy Premium Calculator WEB API

### Built with
* Java 8
* Spring Boot 2.3.5
* Build tool: Maven
* JUnit 5

**Main class:** PremiumCalculatorApplication.java
**Unit Test:** PremiumCalculatorApplicationTests.java

REST API POST endpoint **/api/getPremium** returns calculated Premium for a policy that's passed as a request body (JSON Format).
Request body example:
```json
{
  "policyNumber": "LV20-02-100000-5",
  "policyStatus": "APPROVED",
  "policyObjects": [
    {
    	"name": "Home",
  		"subObjects": [{"name": "object nr1", "sum": 250.0, "riskType": "FIRE"}, 
                       {"name": "object nr1", "sum": 100.0, "riskType": "THEFT"}]
    },
    {
    	"name": "Garage",
  		"subObjects": [{"name": "object nr1", "sum": 250.0, "riskType": "FIRE"}, 
                       {"name": "object nr1", "sum": 2.51, "riskType": "THEFT"}]
    }
  ]
}
```

### Premium calculation logic: PremiumCalculator.calculate(Policy policy)
Method groups all sub-objects by their risk type and calculates the respective sum.
Premium amount is equal to the sum of each risk type sum multiplied by the coefficient of the respective risk type.

Defintion of Risk types and their coefficient logic is located in RiskType enum.
When it is necessary to extend the system with additional risk types, one must merely edit the RiskType enum without worrying about calculation logic.