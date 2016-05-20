# HypothesisPHP
A simple PHP wrapper for the Hypothes.is REST API

The REST API is documented at http://h.readthedocs.io/en/latest/api.html.
You can get an access token at https://hypothes.is/profile/developer.

Example:

    $token = '(put your access token here)';
    
    require_once('Hypothesis.inc.php');
    $hypothesis = new HypothesisAPI();
    
    // Search for annotations by asmecher containing the text "implausible"
    print_r($hypothesis->search(array('user' => 'asmecher', 'text' => 'implausible'), $token));
    
    // Create a new annotation
    $hypothesis->create(array(
      'uri' => '(URL to annotate)',
      'user' => '(hypothes.is username)',
      'permissions' => array(
        'read' => array('group:__world__'),
        'update' => array('acct:(email address)'),
        'delete' => array('acct:(email address)'),
        'admin' => array('acct:(email address)'),
      ),
      'text' => 'Annotation body',
    ), $token);
    
    // Delete the newly-created annotation
    $hypothesis->delete($response->id);
