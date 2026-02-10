---
layout: archive
title: "Membership Form"
permalink: /form/
published: true
---

<form id="membershipForm" method="POST">
  <p>
    Country code (if outside North America)<br>
    <input maxlength="4" name="CountryCode" size="4" type="text">
  </p>

  <table border="0" width="100%">
    <tbody>
      <tr>
        <td width="25%">First Name*</td>
        <td width="50%"><input maxlength="30" name="FirstName" size="30" type="text" required></td>
      </tr>

      <tr>
        <td>Last Name*</td>
        <td><input maxlength="30" name="LastName" size="30" type="text" required></td>
      </tr>

      <tr>
        <td>Department</td>
        <td><input maxlength="40" name="Department" size="30" type="text"></td>
      </tr>

      <tr>
        <td>College or University</td>
        <td><input maxlength="40" name="University" size="30" type="text"></td>
      </tr>

      <tr>
        <td colspan="2" align="center">
          <em>(Your JSE subscription will be sent to this address. You can use a different billing address at PayPal.)</em>
        </td>
      </tr>

      <tr>
        <td>Address*</td>
        <td><input maxlength="40" name="AddrLine" size="30" type="text" required></td>
      </tr>

      <tr>
        <td>City*</td>
        <td><input maxlength="40" name="City" size="30" type="text" required></td>
      </tr>

      <tr>
        <td>State*</td>
        <td><input maxlength="2" name="State" size="2" type="text" required></td>
      </tr>

      <tr>
        <td>ZIP Code*</td>
        <td><input maxlength="10" name="ZIP" size="10" type="text" required></td>
      </tr>

      <tr>
        <td>Phone (10 digits, no dashes)</td>
        <td><input maxlength="10" name="Phone" size="10" type="text"></td>
      </tr>

      <tr>
        <td>Email Address*</td>
        <td><input maxlength="256" name="mailfrom" size="30" type="email" required></td>
      </tr>

      <tr>
        <td>Student</td>
        <td><input name="Student" type="checkbox" value="Yes"></td>
      </tr>
    </tbody>
  </table>

  <!-- Optional: helps you identify the submission -->
  <input type="hidden" name="_subject" value="New NAASE Membership Submission">

  <!-- Spam honeypot -->
  <input type="text" name="_gotcha" style="display:none">

  <p>
    <!-- IMPORTANT: button type is BUTTON (not submit) so the browser won't navigate to Formspree -->
    <button id="submitBtn" type="button">Continue to Payment</button>
    <span id="status" style="margin-left:10px; font-weight:600;"></span>
  </p>

  <p style="margin-top:6px;">
    If you have trouble submitting, you can proceed directly to payment here:
    <a href="/payment/">/payment/</a>
  </p>
</form>

<script>
  (function () {
    const FORMSPREE_ENDPOINT = "https://formspree.io/f/meeleqrr";
    const form = document.getElementById("membershipForm");
    const btn = document.getElementById("submitBtn");
    const statusEl = document.getElementById("status");

    btn.addEventListener("click", async function () {
      // Use built-in browser validation (required fields, email format, etc.)
      if (!form.reportValidity()) return;

      statusEl.textContent = "Submitting…";
      btn.disabled = true;

      try {
        const formData = new FormData(form);

        const resp = await fetch(FORMSPREE_ENDPOINT, {
          method: "POST",
          body: formData,
          headers: { "Accept": "application/json" }
        });

        if (!resp.ok) throw new Error("Formspree error");

        // Redirect to your payment page (this serves /payment/index.html)
        window.location.assign("/payment/");
      } catch (e) {
        statusEl.textContent = "Submission failed. Please try again, or use the payment link.";
        btn.disabled = false;
      }
    });
  })();
</script>

