# Capacity planning

##Capacity planning details
View detailed forecasts about the capacity needs of one or more of your monitored resources. By using past metrics, advanced formulas, and your own input and customized time ranges, you can project, chart, and report on future capacity usage.

Capacity projections are based on the historical metadata of a resource. The actual, future capacity of usage of resources might vary because of different factors and events in your environment over the selected time range. If historical metadata is not available for more than 7 days in the past, no projections are displayed.

##Forecasting Timeframe
**Past date** -
Specify how far in the past to use metadata for the capacity projection. In general, the further in the past that you select, the more metadata that is used in the calculations, which can help aid the capacity projection.

By default, the past date is one year before today’s date. If metadata is unavailable at the selected past date, metadata is used from the date when it is first available. The minimum past date is 7 days before today's date; the maximum past date is 2 years before today's date.

**Future date** -
Specify how far into the future that you want to project capacity usage. By default, the future date is one year from today’s date.

##Forecast Summary

Forecast your future capacity needs.

**Baseline Growth Forecast**
These metrics show your future capacity needs based on an analysis of your historical capacity usage.
**Expected Growth Forecast**
Customize the forecast so that the capacity growth projections are based on a value that you specify. For example, if you expect a 10% increase in your capacity needs by the future date, enter 10% to see metric values that reflect the expected growth.
The following metrics are shown for each capacity forecast:
**Capacity Limit**
The future capacity limit of the storage system or pool (in GiB) based on the original limit that was set. For example, if the capacity limit was set to 80% and the projected used capacity is 100 GiB, the value 80.00 GiB is displayed. If capacity limit value is not set, then the forecast capacity limit is 100 %.
**Capacity Limit Reached**
The date when the specified capacity limit for the storage system will be reached based on historical analysis.
**Compression Ratio**
The ratio of the uncompressed data size to the compressed data size for the entire storage system. This value is blank if the storage system contains at least one pool that uses compressing Flash Core Module (FCM) drives and also contains at least one compressed volume in any type of pool.
**Forecasted Growth**
The forecasted growth of your capacity based on the historical capacity usage during the time range that you selected. Use the capacity value and percentage to get an AIOPs-generated prediction of your potential capacity needs so you can start planning future storage purchases. To forecast capacity growth, the following formulas are used:
*Forecasted Growth (GiB) = Forecasted Used Capacity - Used Capacity Today*

*Forecasted Growth (%) = 100 * (Forecasted Growth / Used Capacity Today)*

###Forecasted Used Capacity
#Baseline Growth Forecast
The forecasted capacity usage based on the historical capacity usage during the time range that you selected. Use this value to help gauge your future capacity usage and potential capacity needs.
**Expected Growth Forecast**
The forecasted capacity usage based on the growth that you expect during the selected time range. Use this value to help gauge your future capacity usage and potential capacity needs. To forecast used capacity, the following formula is used:
Forecasted Used Capacity = Used Capacity Today + (Used Capacity Today * Forecasted Growth %)/100

**Expected Growth**
The growth expected based on the capacity during the selected time range and user input. The following formula is used to find the expected growth:
Expected Growth = Used Capacity Today + Used Capacity Today * Expected Growth (user input)/100

**Forecasted Written Capacity**
The forecasted amount of capacity during the selected time range that will be written to the volumes in a pool before inline disk compression is applied.

Forecasted Written Capacity = Forecasted Used Capacity * Compression Ratio

**Surplus or Deficit**
The amount of the capacity that is excess or deficit when compared to Forecasted Used Capacity. The value can be positive or negative.

*Surplus or Deficit = Capacity Limit - Forecasted Used Capacity*

**Used Capacity Today**
The physical capacity that is used on all of the volumes, which includes thin-provisioned, compressed, and standard-provisioned volumes, in the pools on the storage system. If the empty thin-provisioned volumes are removed from the pools, it might not change the value of used capacity, which represents that the thin-provisioning and data reduction are combined.

**Used Written Capacity**
The amount of capacity that is written to the volumes in a pool before inline disk compression is applied. If a pool is not compressed, this value is the same as Used Capacity.

##Growth Projection chart
Based on the time frame selected and historic capacity metadata of the selected device, a chart will be projected in this section. Once you enter the Forecasted Growth percentage in Expected Growth Forecast column, a new line appears in the chart.

Hover the mouse pointer over lines in the chart to view a snapshot of Forecasted Capacity % and Used Capacity at specific time. For example, to view the capacity growth for a selected storage system for selected time frame, hover over the corresponding metadata collection point on the line.
**Capacity Limit**
Dotted line represents the predefined capacity limit of the storage device.
**Historical Growth**
Represents the historical growth of the capacity for selected past date.
**Baseline Growth**
Represents the historical growth of the capacity for selected future date.
**Used Capacity**
Represents the used capacity of the storage system..
**Expected Growth**
Represents the forecast of the expected growth for the given Forecasted Growth percentage.
##Multiple Devices Forecast
If you select multiple devices, the Forecast summary divides in to Aggregate and Breakdown tabs. If one of the selected devices is not having any metadata, the displayed values belongs to other devices.
Restriction: Multiple selection is not applicable for pools by tier and STaaS environments.
**Aggregate**
The metrics are same which were shown while we select the single storage device. The values shown in the metrics are the combined values of all selected devices.
If you enter the value in Forecasted Growth (%) of Expected Growth Forecast column, the metric values and the projections shown in the Growth Projection chart are combined values of all selected devices.

**BreakDown**
The metrics of the individual devices are shown in this section. If you select each device, the predictive capacity chart of that device is shown on Growth Projection chart.