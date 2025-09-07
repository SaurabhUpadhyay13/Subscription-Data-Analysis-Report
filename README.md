# Subscription-Data-Analysis-Report New


<!DOCTYPE html>
<html>
<head>
    <title>Subscription Data Analysis Report</title>
</head>
<body>
[Link to Interactive Dashboard](http://127.0.0.1:8050/)
<h1>Subscription Data Analysis Report</h1>

<h2>Introduction</h2>
<p>This report provides a comprehensive analysis of user subscription data, leveraging Python, pandas for data manipulation, and Plotly for interactive dashboards. The dataset includes critical features such as User ID, Subscription Type, Monthly Revenue, Join Date, Last Payment Date, Country, Age, Gender, Device, and Plan Duration. A critical aspect of the analysis involved addressing formatting issues in the 'Join Date' and 'Last Payment Date' columns to ensure accurate insights.</p>

<h2>Dataset Overview</h2>
<p>The dataset encompasses a variety of features vital for understanding user subscription patterns. The key attributes include User ID, Subscription Type, Monthly Revenue, Join Date, Last Payment Date, Country, Age, Gender, Device, and Plan Duration. However, the analysis faced a significant challenge in dealing with formatting issues within the 'Join Date' and 'Last Payment Date' columns. The dates exhibited inconsistencies, with some entries aligned to the left and others to the right.</p>

<h3>Addressing Formatting Challenges in Date Columns</h3>
<p>To ensure precise analysis, it was imperative to transform the date columns into a consistent 'MM-DD-YYYY' format. The Power Query tool emerged as a valuable resource for resolving these formatting discrepancies. The following steps were undertaken to tackle the date-related challenges:</p>

<ol>
    <li>Delimitation: The initial step involved using a delimiter to separate the date components (month, day, year) within the 'Join Date' and 'Last Payment Date' columns. This separation allowed for better manipulation and restructuring of the date information.</li>
    <li>Merging and Formatting: Subsequently, the separated components were merged into a unified format of 'MM-DD-YYYY.' Leveraging Power Query's capabilities, this merging process was executed seamlessly. The resultant date format ensured consistency across all entries, overcoming the initial challenges posed by varying alignments and formats.</li>
    <li>Conversion to Date Type: The final critical step involved converting the formatted dates into a uniform date and time data type. This not only facilitated accurate chronological ordering but also enabled subsequent analyses that relied on temporal insights.</li>
</ol>

<h2>User Demographics Visualization</h2>
<h3>Total Gender Count by Country</h3>
<p>To provide insights into user demographics, a bar chart displaying the number of users by gender was generated. The visualization allows for filtering by country through a dropdown.</p>

<pre>
<code>
gender_count_by_country = df.groupby('Gender')['Country'].value_counts().unstack()
</code>
</pre>

<pre>
<code>
Gender  Country
Female  Spain             233
        United States     225
        Canada            157
        Brazil             95
        Germany            94
        United Kingdom     93
        France             91
        Italy              91
        Australia          89
        Mexico             89
Male    United States     226
        Spain             218
        Canada            160
        Australia          94
        Mexico             94
        France             92
        Italy              92
        United Kingdom     90
        Germany            89
        Brazil             88
</code>
</pre>

<h4>Insights:</h4>
<ul>
    <li>The United States has the highest number of subscription users.</li>
    <li>Spain leads in the Female category, while the United States dominates in the Male category.</li>
</ul>


![newplot (3)](https://github.com/SaurabhUpadhyay13/Subscription-Data-Analysis-Report/assets/126344704/e5f34c68-dac2-45ce-92b0-7816a6983c0a)

<h2>Subscription Overview</h2>
<p>A pie chart was employed to showcase the proportion of each subscription type, with sliders for filtering data by plan duration and dropdowns for gender and country, providing enhanced filtering capabilities.</p>

<pre>
<code>
subscription_count = df['Subscription Type'].value_counts()
</code>
</pre>

<h4>Insights:</h4>
<ul>
    <li>Basic plans are the most popular, with 999 subscriptions, followed by Standard (768) and Premium (733).</li>
    <li>Combining Standard and Premium plans exceeds the number of Basic subscriptions, indicating potential growth in higher-tier plans.</li>
</ul>

![newplot (2)](https://github.com/SaurabhUpadhyay13/Subscription-Data-Analysis-Report/assets/126344704/686db04f-46ac-4c88-b1c9-ad3e6e7608ae)


<p>The addition of dropdowns for gender and country further refines the analysis, allowing for a more granular exploration of subscription patterns. Users can now filter the data based on these additional parameters, providing a comprehensive view of subscription preferences across different demographic segments and geographic locations.</p>

<h2>Monthly Revenue Trend</h2>
<h3>Total Monthly Revenue Over Time</h3>
<p>A line chart illustrates the total monthly revenue over time, allowing for toggling between overall and segmented views by subscription type revenue.</p>

<pre>
<code>
total_revenue_by_country = df.groupby('Country')['Monthly Revenue'].sum().reset_index(name='Total Revenue')
</code>
</pre>

<pre>
<code>
Country  Total Revenue
0       Australia           2271
1          Brazil           2285
2          Canada           3950
3          France           2307
4         Germany           2260
5           Italy           2317
6          Mexico           2237
7           Spain           5662
8  United Kingdom           2318
9   United States           5664
</code>
</pre>

<h4>Insights:</h4>
<ul>
    <li>The United States consistently contributes the highest revenue, followed by Spain.</li>
    <li>European countries and the UK collectively contribute a significant portion of revenue, suggesting growth opportunities in these regions.</li>
</ul>

![newplot (1)](https://github.com/SaurabhUpadhyay13/Subscription-Data-Analysis-Report/assets/126344704/4d38a86c-87b7-459b-bea0-9e76c384109d)


<h2>Additional Charts</h2>
<p>Additional charts were introduced, offering insights into user preferences and revenue-generating areas. These charts can be toggled using a dropdown menu:</p>

<h3>Device Count for Each Device:</h3>
<pre>
<code>
device_count = df.groupby('Device').size().reset_index(name='Device Count')
</code>
</pre>

<pre>
<code>
Device  Device Count
0      Laptop           636
1    Smart TV           610
2  Smartphone           621
3      Tablet           633
</code>
</pre>

<h3>Device Count by Gender:</h3>
<pre>
<code>
device_count_gender = df.groupby(['Device', 'Gender']).size().reset_index(name='Device Count')
</code>
</pre>

<pre>
<code>
Device  Gender  Device Count
0      Laptop  Female           329
1      Laptop    Male           307
2    Smart TV  Female           305
3    Smart TV    Male           305
4  Smartphone  Female           300
5  Smartphone    Male           321
6      Tablet  Female           323
7      Tablet    Male           310
</code>
</pre>

<h3>Total Revenue by Country:</h3>
<pre>
<code>
total_revenue_by_country = df.groupby('Country')['Monthly Revenue'].sum().reset_index(name='Total Revenue')
</code>
</pre>

<pre>
<code>
Country  Total Revenue
0       Australia           2271
1          Brazil           2285
2          Canada           3950
3          France           2307
4         Germany           2260
5           Italy           2317
6          Mexico           2237
7           Spain           5662
8  United Kingdom           2318
9   United States           5664
</code>
</pre>

<h4>Insights:</h4>
<ul>
    <li>Insights from device count and revenue analyses can optimize subscription plans, aligning them with user preferences.</li>
    <li>Revenue breakdowns by country and gender provide valuable information for tailoring marketing strategies to specific demographics.</li>
</ul>

![newplot](https://github.com/SaurabhUpadhyay13/Subscription-Data-Analysis-Report/assets/126344704/8a9bc27e-71c3-4818-ac79-c245e5b0b1c3)


<h2>Business Insights and Recommendations</h2>
<h3>User Demographics:</h3>
<ul>
    <li>Tailor marketing strategies in countries with high user engagement, such as the United States and Spain.</li>
    <li>Align promotional efforts with observed variations in subscription choices based on gender.</li>
</ul>

<h3>Subscription Overview:</h3>
<ul>
    <li>Enhance benefits or introduce new features to attract Basic plan users towards higher-tier plans.</li>
    <li>Capitalize on the popularity of Standard and Premium plans by optimizing their offerings.</li>
</ul>

<h3>Monthly Revenue Trend:</h3>
<ul>
    <li>Prioritize business expansion and marketing efforts in countries with untapped potential.</li>
    <li>Explore partnerships or campaigns to increase brand visibility in European countries and the UK.</li>
</ul>

<h3>Additional Charts:</h3>
<ul>
    <li>Utilize insights from device count and revenue analyses to optimize subscription plans.</li>
    <li>Tailor marketing strategies for specific demographics using revenue breakdowns by country and gender.</li>
</ul>

<p><strong>Business Insights and Recommendations:</strong></p>
<ul>
    <li>Tailor marketing strategies in countries with high user engagement, such as the United States and Spain.</li>
    <li>Enhance benefits or introduce new features to attract Basic plan users towards higher-tier plans.</li>
    <li>Prioritize business expansion and marketing efforts in countries with untapped potential.</li>
    <li>Utilize insights from device count and revenue analyses to optimize subscription plans.</li>
    <li>Tailor marketing strategies for specific demographics using revenue breakdowns by country and gender.</li>
</ul>

</body>
</html>
