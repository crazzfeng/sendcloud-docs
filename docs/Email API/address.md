---
title: Address
excerpt: >-
  Manage email lists for bulk sending using the API and collect email addresses
  of potential users on your website using the subscription feature.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Address Management

Manage your contact email addresses effectively with powerful tools for bulk campaigns and lead collection. Choose between **Address Lists** for marketing campaigns or **Subscription Management** for growing your subscriber base.

# Address Lists


  
    The Address List function is your powerhouse for **bulk email sending** scenarios, including marketing campaigns, newsletters, and automated sequences. It supports advanced variable replacement for personalized messaging at scale.

    ## Key Features

    <Cards columns={3}>
      <Card title="Bulk Import">
        Upload thousands of contacts instantly with support for multiple file formats and automatic validation.
      </Card>

      <Card title="Variable Replacement">
        Personalize emails with custom variables like %name%, %company%, %location% for higher engagement.
      </Card>

      <Card title="API Integration">
        Seamlessly integrate with your existing systems using our robust API and unique list aliases.
      </Card>
    </Cards>

    ## File Upload & Formats

    <Accordion title="Supported File Formats">
      **Supported Formats:**

      * **.CSV** (Comma Separated Values) - Recommended
      * **.TXT** (Plain Text Files)
      * **.XLS** (Excel 97-2003)
      * **.XLSX** (Excel 2007+)

      **CSV Format Best Practices:**

      ```
      email,name,company,location
      john@example.com,John Doe,Acme Corp,New York
      jane@example.com,Jane Smith,Tech Inc,California
      ```

      **File Structure Tips:**

      * First column: Email addresses (required)
      * Additional columns: Custom variables for personalization
      * Header row: Use descriptive names that match your email templates
      * Encoding: Use UTF-8 to support international characters
    </Accordion>

    <Accordion title="Upload Processing Details">
      **Automatic Processing Features:**

      ✅ **Smart Deduplication**: Removes duplicate email addresses across uploads
      ✅ **Format Validation**: Verifies email address syntax and domain validity\
      ✅ **Data Sanitization**: Cleans up formatting issues and extra whitespace
      ✅ **Progress Tracking**: Real-time upload status and error reporting

      **Processing Limits:**

      * Maximum file size: **100MB** per upload
      * Maximum contacts per list: **1 million addresses**
    </Accordion>

  
  

##Subscription Management


    Transform your website visitors into engaged subscribers with our easy-to-implement subscription system. Collect leads legally and efficiently while maintaining compliance with privacy regulations.

    ## Implementation Process

    <Cards columns={1}>
      <Card title="1. Generate Your Code" icon="code">
        **Get Custom JavaScript**

        Navigate to Subscription Management in your dashboard and generate a unique JavaScript snippet tailored to your target Address List.
      </Card>

      <Card title="2. Website Integration" icon="globe">
        **Strategic Placement**

        Embed your subscription form in high-conversion areas:

        * Homepage header or footer
        * Blog post sidebars
        * About page
        * Pop-up modals (with timing controls)
        * Thank you pages
      </Card>

      <Card title="3. Visual Display" icon="eye">
        **User Experience**

        The form automatically displays with:

        * Clean, responsive design
        * Mobile-optimized layout
        * Accessible form controls
        * Real-time validation feedback
      </Card>

      <Card title="4. Data Collection" icon="database">
        **Automated Processing**

        Collected emails are instantly:

        * Added to your target Address List
        * Validated for format and deliverability
        * Timestamped for tracking
        * Ready for your next campaign
      </Card>
    </Cards>

   

    ## Implementation Example

    <Accordion title="Complete Setup Walkthrough" icon="play-circle">
      **Step-by-Step Implementation:**

      1. **Create Target List**
         * Go to Address Lists → New List
         * Name: "Website Subscribers 2024"
         * Alias: `website_subscribers_2024`

      2. **Generate Subscription Code**
         * Navigate to Subscription Management
         * Select your target list
         * Customize form appearance
         * Copy generated JavaScript

      3. **Website Integration**
         Embed the code into the required page

      4. **Test & Optimize**
         * Submit test email addresses
         * Verify list population
         * Check email confirmations
         * Monitor conversion rates
    </Accordion>

    <Accordion title="Best Practices for Lead Generation" icon="lightbulb">
      **Conversion Optimization Tips:**

      **Incentive Strategies:**

      * Offer exclusive content or discounts
      * Promise valuable weekly insights
      * Provide free resources or tools
      * Create urgency with limited-time offers

      **Form Placement:**

      * Above the fold on high-traffic pages
      * End of valuable blog posts
      * Exit-intent popups
      * Social media landing pages

      **Content Strategy:**

      * Clear value proposition
      * Minimal required fields
      * Strong call-to-action buttons
      * Social proof and testimonials
    </Accordion>
