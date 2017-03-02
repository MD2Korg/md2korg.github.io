<script src='http://ajax.googleapis.com/ajax/libs/jquery/1.10.1/jquery.min.js' type='text/javascript'></script>
<script type='text/javascript'>

  var projectId;
  function executeTrackerApiFetch() {
    // get parameters
    var token = 'a0a5ef1b94467ef44d393b7e2d01569d';
    projectId = 1982081;

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
  }
</script>

# Feedback

<form>
  <p>
    <label for='token'>Short Description</label>
    <input type='text' id='name' />
  </p><p>
  <label for='project_id'>Details:</label>
  <textarea rows="8" id='description'></textarea>
</p>
</form>

<a href='#' id='doit_link'>Submit Feedback</a>

<div style='margin:40px'>
  <p id='result_title'></p>
  <ul id='result_area'>
  </ul>
</div>
