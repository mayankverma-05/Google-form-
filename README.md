# Google-form-
Asking for name , class , roll no to students:- 
/**
 * Creates a Google Form for student information:
 * - Full Name (short answer, required)
 * - Class (short answer, required)
 * - Roll Number (short answer, required; numeric range validation)
 *
 * After running, check the Apps Script Logs (View → Logs) for the form URLs.
 */
function createStudentForm() {
  // Create the form
  var form = FormApp.create('Student Information Form')
    .setDescription('Please fill in your details. This form collects student name, class and roll number.');

  // Full Name (required)
  form.addTextItem()
    .setTitle('Full Name')
    .setHelpText('Enter your full name')
    .setRequired(true);

  // Class (required)
  form.addTextItem()
    .setTitle('Class')
    .setHelpText('e.g., Grade 10 / 12A / Year 9')
    .setRequired(true);

  // Roll Number (required) with numeric validation (0..999999)
  var rollItem = form.addTextItem()
    .setTitle('Roll Number')
    .setHelpText('Enter your roll number (digits only)')
    .setRequired(true);

  var rollValidation = FormApp.createTextValidation()
    .requireNumberBetween(0, 999999)
    .setHelpText('Please enter a numeric roll number (digits only).')
    .build();

  rollItem.setValidation(rollValidation);

  // Optional: customize confirmation message
  form.setConfirmationMessage('Thanks — your response has been recorded.');

  // Log the form URLs
  Logger.log('Form URL (for respondents): ' + form.getPublishedUrl());
  Logger.log('Form Edit URL (for owner): ' + form.getEditUrl());

  // Also return the URLs for immediate use when called from another script
  return {
    publishedUrl: form.getPublishedUrl(),
    editUrl: form.getEditUrl()
  };
}
