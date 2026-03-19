---
layout: default
title: Dataset
---

<div class="section">
  <h2>Source</h2>

  <p>
    This project uses the <strong>Major Power Outages in the United States</strong> dataset from Purdue University's Laboratory for Advancing Sustainable Critical Infrastructure (LASCI).
    It contains historical records of large power outages across U.S. states along with information about outage causes, electricity demand, and demographic characteristics.
  </p>

  <p>
    Dataset source:<br>
    <a href="https://engineering.purdue.edu/LASCI/research-data/outages">Power Outage Dataset</a>
  </p>

  <p>
    Data dictionary:<br>
    <a href="https://www.sciencedirect.com/science/article/pii/S2352340918307182">Data Dictionary</a>
  </p>
</div>

<div class="section">
  <h2>Overview</h2>

  <p>
    A major outage in this dataset refers to an event that affected at least 50,000 customers or caused at least 300 MW of unplanned firm load loss.
  </p>

  <p>
    The data combines outage event information with state-level climate, electricity consumption, economic, and land-use characteristics.
  </p>
</div>

<div class="section">
  <h2>What the Dataset Includes</h2>

  <ul>
    <li>when the outage happened</li>
    <li>where the outage occurred</li>
    <li>how long the outage lasted</li>
    <li>how many customers were affected</li>
    <li>the reported cause of the outage</li>
    <li>electricity demand loss</li>
    <li>state-level electricity pricing and consumption</li>
    <li>regional economic and demographic characteristics</li>
  </ul>
</div>

<div class="section">
  <h2>Important Variables</h2>

  <table>
    <tr><th>Variable</th><th>Description</th></tr>
    <tr><td>YEAR</td><td>Year the outage occurred</td></tr>
    <tr><td>MONTH</td><td>Month the outage occurred</td></tr>
    <tr><td>U.S._STATE</td><td>State where the outage occurred</td></tr>
    <tr><td>NERC.REGION</td><td>NERC region involved</td></tr>
    <tr><td>OUTAGE.START.DATE</td><td>Start date</td></tr>
    <tr><td>OUTAGE.START.TIME</td><td>Start time</td></tr>
    <tr><td>OUTAGE.RESTORATION.DATE</td><td>End date</td></tr>
    <tr><td>OUTAGE.RESTORATION.TIME</td><td>End time</td></tr>
    <tr><td>OUTAGE.DURATION</td><td>Duration (minutes)</td></tr>
    <tr><td>CUSTOMERS.AFFECTED</td><td>Customers impacted</td></tr>
    <tr><td>DEMAND.LOSS.MW</td><td>Demand loss</td></tr>
    <tr><td>CAUSE.CATEGORY</td><td>Outage cause</td></tr>
    <tr><td>CLIMATE.CATEGORY</td><td>Climate type</td></tr>
  </table>
</div>

<div class="section">
  <h2>Data Cleaning</h2>

  <ul>
    <li>Removed the first row containing units</li>
    <li>Standardized column names</li>
    <li>Converted date/time into usable formats</li>
    <li>Handled missing values</li>
    <li>Selected relevant variables for modeling</li>
  </ul>
</div>

<div class="section">
  <h2>Limitations</h2>

  <p>
    Some variables contain missing values, and some outage causes are more detailed than others. Because the data is aggregated from several public sources, reporting consistency may vary across states and years.
  </p>
</div>
