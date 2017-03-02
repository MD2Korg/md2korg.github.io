<script src='http://ajax.googleapis.com/ajax/libs/jquery/1.10.1/jquery.min.js' type='text/javascript'></script>

# Feedback
Please provide as many details as possible when reporting bugs or other feedback.

## mCerebrum and Cerebral Cortex

<div id="md2kform">
<form class="form-horizontal">
<fieldset>

<!-- Form Name -->
<legend>Feedback Form</legend>

<!-- Text input-->
<div class="form-group">
  <label class="col-md-4 control-label" for="textinput">Short Description</label>
  <div class="col-md-4">
  <input id="name" name="textinput" type="text" placeholder="placeholder" class="form-control input-md" required="">

  </div>
</div>

<!-- Textarea -->
<div class="form-group">
  <label class="col-md-4 control-label" for="textarea">Details</label>
  <div class="col-md-4">
    <textarea class="form-control" id="description" name="textarea"></textarea>
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

    object = {
              name: $('#name').val(),
              description: $('#description').val(),
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
