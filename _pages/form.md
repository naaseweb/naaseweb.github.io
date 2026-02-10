---
layout: archive
title: "Membership Form"
permalink: /form/
published: true
---

<form id="membershipForm"
      action="https://formspree.io/f/meeleqrr"
      method="POST">

<!-- … your existing fields … -->

<!-- Redirect: set dynamically to current domain + /payment/ -->
<input type="hidden" id="_next" name="_next" value="">

<input type="hidden" name="_subject" value="New NAASE Membership Submission">
<input type="text" name="_gotcha" style="display:none">

<p>
  <input type="submit" value="Continue to Payment">
</p>

</form>

<script>
  // Make Formspree redirect work on both dev and production domains
  document.getElementById('_next').value = window.location.origin + '/payment/';
</script>


<tr>
<td>Email Address*</td>
<td>
<input maxlength="256" name="mailfrom" size="30" type="email" required>
</td>
</tr>

<tr>
<td>Student</td>
<td>
<input name="Student" type="checkbox" value="Yes">
</td>
</tr>

</tbody>
</table>

<!-- Redirect to your site payment page (RELATIVE — works on all domains) -->
<input type="hidden" name="_next" value="/payment/">

<!-- Email subject line -->
<input type="hidden" name="_subject" value="New NAASE Membership Submission">

<!-- Spam honeypot -->
<input type="text" name="_gotcha" style="display:none">

<p>
<input type="submit" value="Continue to Payment">
</p>

</form>
