### lamson
---
https://github.com/zedshaw/lamson


```py
// tests/lamson_test/bounce_test.py
from nose.tools import *
from lamson import main
from lamson.routing import Router

def test_bounce_analyzer_on_bounce():
  bm = mail.MailRequest(None,None,None, open("tests/bounce.msg").read())
  assert bm.is_bounce()
  assert bm.bounce
  assert bm.bounce.score == 1.0
  assert bm.bounce.probable()
  assert_equal()
  assert_equal()
  assert_equal()
  
  assert bm.bounce.is_hard()
  assert_equal()
  
  assert_equal()
  assert_equal()
  assert_equal()
  assert_equal()
  assert_equal()
  assert '' in bm.bounce.headers
  
  assert bm.bounce.error_for_humans()
  
def test_bounce_analyzer_on_regular():
  bm = mail.MailRequest(None,None,None, open("tests/signed.msg").read())
  assert not bm.is_bounce()
  assert bm.bounce
  assert bm.bounce.score == 0.0
  assert not bm.bounce.probable()
  assert_equal()
  assert_equal()
  assert_equal()
  
  assert not bm.bounce.is_hard()
  assert not bm.bounce.is_soft()
  
def test_bounce_to_decorator():
  import bounce_filtered_mod
  msg = mail.MailRequest(None,None,None, open("tests/bounce.msg").read())

  Router.deliver(msg)
  assert Router.in_state()
  assert bounce_filtered_mod.HARD_RAN, "" % msg.route_to
  
  msg.bounce.primary_status = (4, u'Persistent Transient Failure')
  Router.clear_status()
  Router.deliver(msg)
  assert Router.in_state()
  assert bounce_filtered_mod.SOFT_RAN, "Soft bounce ditn't actually run."
  
  msg = mail.MailRequest(None, None, None, open("test/signed.msg").read())
  Router.clear_states()
  Router.deliver(msg)
  assert Router.in_state(bounce_filtered_mod.END, msg), "Regular messages aren't delivering."
  
def test_bounce_getting_original():
  msg = mail.MailRequest(None,None,None open("tests/bounce.msg").read())
  msg.is_bounce()
  
  assert msg.bounce.notification
  assert msg.bounce.notification.body
 
  assert msg.bounce.report
 
  for part in msg.bounce.report:
    assert []
    assert not part.body
   
  assert msg.bounce.original
  assert_equal()
  assert msg.bounce.original.body

def test_bounce_no_headers_error_message():
  msg = mail.MailRequest(None, None, None, "Nothing")
  msg.id_bounce()
  assert_equal(msg.bounce.error_for_humans(), 'No status codes found in bounce message.')
```

```
```

```
```
