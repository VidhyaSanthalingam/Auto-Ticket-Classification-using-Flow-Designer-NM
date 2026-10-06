// AUTO TICKET CLASSIFICATION USING FLOW DESIGNER
// ServiceNow - Incident Table

(function autoTicketClassification(current) {

    // Step 1 & 2: Get Incident Details
    var shortDesc = (current.short_description || "").toString().toLowerCase();
    var description = (current.description || "").toString().toLowerCase();

    var ticketText = shortDesc + " " + description;

    // Step 3: Initialize Classification
    var category = "";
    var subcategory = "";
    var assignmentGroup = "";

    // Step 4: Network Ticket
    if (ticketText.indexOf("network") >= 0 ||
        ticketText.indexOf("wifi") >= 0 ||
        ticketText.indexOf("internet") >= 0) {

        category = "Network";
        subcategory = "Connectivity";
        assignmentGroup = "Network Team";

    }

    // Step 5: Password/Login Ticket
    else if (ticketText.indexOf("password") >= 0 ||
             ticketText.indexOf("login") >= 0 ||
             ticketText.indexOf("account") >= 0) {

        category = "Software";
        subcategory = "Login";
        assignmentGroup = "Service Desk";

    }

    // Step 6: Hardware Ticket
    else if (ticketText.indexOf("laptop") >= 0 ||
             ticketText.indexOf("keyboard") >= 0 ||
             ticketText.indexOf("mouse") >= 0 ||
             ticketText.indexOf("printer") >= 0) {

        category = "Hardware";
        subcategory = "Computer";
        assignmentGroup = "Hardware Team";

    }

    // Step 7: Software Ticket
    else if (ticketText.indexOf("software") >= 0 ||
             ticketText.indexOf("application") >= 0 ||
             ticketText.indexOf("app") >= 0) {

        category = "Software";
        subcategory = "Application";
        assignmentGroup = "Application Support";

    }

    // Step 8: Default Classification
    else {

        category = "Inquiry";
        subcategory = "General";
        assignmentGroup = "Service Desk";
    }

    // Step 9: Update Incident
    current.category = category;
    current.subcategory = subcategory;
    current.assignment_group.setDisplayValue(assignmentGroup);

    // Step 10: Save Updated Incident
    current.update();

})(current);
