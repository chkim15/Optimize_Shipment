# Optimization Tool for Shipment Quantities

#### Problem: We are often asked to quote prices based on which products and how much quantities our customers want. There are many factors to consider before making the decision, but currently we do not have an easy method to solve it.

#### This is a tool that helps us to find the optimal quantities of requested items for shipment. Below are what need to be considered:

- The total volume must not exceed a container's capacity (containers: 20ft, 40ft, 40hq).  
- There might be some production capacity for certain products, so the shipment quantity cannot go over that.  
- 'Demand' indicates what the customer is requesting for quote. This tool will adjust quantities from this 'Demand' while keeping the constraints and objective.
- The objective is to maximize the profit.
