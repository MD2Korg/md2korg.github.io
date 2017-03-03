<script src='http://ajax.googleapis.com/ajax/libs/jquery/1.10.1/jquery.min.js' type='text/javascript'></script>

# Feedback
Please provide as many details as possible when reporting bugs or other feedback.

For a list of current activities and all outstanding issues please see the <a href='https://www.pivotaltracker.com/n/projects/1982081' target='_blank'>issue tracker</a>

## mCerebrum and Cerebral Cortex

<div id="md2kform">
<form class="form-horizontal" id='myform'>
<fieldset>

<!-- Form Name -->
<legend>Feedback Form</legend>

<!-- Multiple Radios -->
<div class="form-group">
  <label class="col-md-4 control-label" for="radios">Choose the type of feedback you are submitting</label>
  <div class="col-md-4">
  <div class="radio">
    <label for="radios-0">
      <input type="radio" name="radios" id="bug_option" value="1" checked="checked">
      Bug Report
    </label>
	</div>
  <div class="radio">
    <label for="radios-1">
      <input type="radio" name="radios" id="feature_option" value="2">
      Feature Request
    </label>
	</div>
  </div>
</div>

<!-- Text input-->
<div class="form-group">
  <label class="col-md-4 control-label" for="textinput">Short Description</label>
  <div class="col-md-4">
  <input id="name" name="textinput" type="text" class="form-control input-md" required>

  </div>
</div>

<!-- Textarea -->
<div class="form-group">
  <label class="col-md-4 control-label" for="textarea">Details</label>
  <div class="col-md-4">
    <textarea class="form-control" id="description" name="textarea" rows="5" placeholder="Please describe the bug or feature with as much detail as appropriate."></textarea>
  </div>
</div>

<!-- Text input-->
<div class="form-group">
  <label class="col-md-4 control-label" for="textinput">Submitter</label>
  <div class="col-md-4">
  <input id="submitter" name="textinput" type="text" placeholder="Your name and email(optional)" class="form-control input-md">

  </div>
</div>

<!-- Button -->
<div class="form-group">
  <label class="col-md-4 control-label" for="singlebutton"></label>
  <div class="col-md-4">
    <button type="button" id="doit_link" name="singlebutton" class="btn btn-primary">Submit Feedback</button>
  </div>
</div>

</fieldset>
</form>
</div>

<div style='margin:40px'>
  <p id='result_title'></p>
  <ul id='result_area'>
  </ul>
</div>


<script type='text/javascript'>

 $(document).ready(function() {

  function executeTrackerApiFetch() {
    // get parameters
    var token = 'a0a5ef1b94467ef44d393b7e2d01569d';
    var projectId = 1982081;

    // compose request URL
    var url = 'https://www.pivotaltracker.com/services/v5';
    url += '/projects/' + projectId;
    url += '/stories';

    var form_selection = $('input[name=radios]:checked', '#myform').val();
    var s_type="feature";
    if (form_selection == 1) {
      s_type = "bug";
    }
    if (form_selection == 2) {
      s_type = "feature";
    }


    var description_string = $('#description').val();
    var submitter = $('#submitter').val()
    if (submitter.length > 0) {
      description_string = submitter + '\n\n' + description_string;
    }

    object = {
              name: $('#name').val(),
              story_type: s_type,
              description: description_string,
             }
    console.log(object)
    // do API request to get story names
    $.ajax({
      type: "POST",
      url: url,
      data: object,
      dataType: "json",
      beforeSend: function(xhr) {
        xhr.setRequestHeader('X-TrackerToken', token);
      }
    }).done(displayTrackerApiResponse);
  }

  function displayTrackerApiResponse(stories) {
    $('#result_title').html('Feedback submitted successfully');
    $('#name').val('');
    $('#description').val('');
  }

  $(function() {
    $('#doit_link').click(executeTrackerApiFetch);
  });
});
</script>
