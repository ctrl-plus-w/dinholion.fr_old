<script setup lang="ts">
const active = ref('')
setTimeout(() => {
  active.value = 'is-active'
}, 750)
</script>

<!--<link href="https://reservation.aqin.io/core/framework/libs/pj/css/pj.bootstrap.min.css" type="text/css" rel="stylesheet" />-->
<!--<link href="https://reservation.aqin.io/index.php?controller=pjFrontEnd&action=pjActionLoadCss" type="text/css" rel="stylesheet" />-->
<!--<script type="text/javascript" src="https://reservation.aqin.io/index.php?controller=pjFrontEnd&action=pjActionLoad"></script>-->

<script lang="ts">
export default {
  mounted() {
    console.log('loaded');

    const addLink = (href: string) => {
      const link = document.createElement('link');
      link.setAttribute('href', href);
      link.setAttribute('type', 'text/css');
      link.setAttribute('rel', 'stylesheet');
      document.head.appendChild(link);
    }

    // const addScript = (src: string) => {
    //   const script = document.createElement('script');
    //   script.setAttribute('src', src);
    //   script.setAttribute('type', 'text/javascript');
    //   document.head.appendChild(script);
    // }

    addLink('https://reservation.aqin.io/core/framework/libs/pj/css/pj.bootstrap.min.css');
    addLink('https://reservation.aqin.io/index.php?controller=pjFrontEnd&action=pjActionLoadCss');
    // addScript('https://reservation.aqin.io/index.php?controller=pjFrontEnd&action=pjActionLoad');

    (function() {
      'use strict'
      var isSafari = /Safari/.test(navigator.userAgent) && /Apple Computer/.test(navigator.vendor),
        loadCssHack = function(url, callback) {
          var link = document.createElement('link')
          link.type = 'text/css'
          link.rel = 'stylesheet'
          link.href = url
          document.getElementsByTagName('head')[0].appendChild(link)
          var img = document.createElement('img')
          img.onerror = function() {
            if (callback && typeof callback === 'function') {
              callback()
            }
          }
          img.src = url
        }, loadRemote = function(url, type, callback) {
          if (type === 'css' && isSafari) {
            loadCssHack(url, callback)
            return
          }
          var _element, _type, _attr, scr, s, element
          switch (type) {
            case 'css':
              _element = 'link'
              _type = 'text/css'
              _attr = 'href'
              break
            case 'js':
              _element = 'script'
              _type = 'text/javascript'
              _attr = 'src'
              break
          }
          scr = document.getElementsByTagName(_element)
          s = scr[scr.length - 1]
          element = document.createElement(_element)
          element.type = _type
          if (type == 'css') {
            element.rel = 'stylesheet'
          }
          if (element.readyState) {
            element.onreadystatechange = function() {
              if (element.readyState == 'loaded' || element.readyState == 'complete') {
                element.onreadystatechange = null
                if (callback && typeof callback === 'function') {
                  callback()
                }
              }
            }
          } else {
            element.onload = function() {
              if (callback && typeof callback === 'function') {
                callback()
              }
            }
          }
          element[_attr] = url
          s.parentNode.insertBefore(element, s.nextSibling)
        }, loadScript = function(url, callback) {
          loadRemote(url, 'js', callback)
        }, loadCss = function(url, callback) {
          loadRemote(url, 'css', callback)
        }, getSessionId = function() {
          return sessionStorage.getItem('session_id') == null ? '' : sessionStorage.getItem('session_id')
        }, createSessionId = function() {
          if (getSessionId() == '') {
            sessionStorage.setItem('session_id', 'pngc03rep76ca3e9tlsmtkar5h')
          }
        }, options = {
          server: 'https://reservation.aqin.io/',
          folder: 'https://reservation.aqin.io/',
          theme: 'theme6',
          index: 3301,
          locale: 2,
          direction: 'ltr',
          week_start: 1,
          momentDateFormat: 'DD.MM.YYYY',
          time_format: 'HH:mm',
          lat: 48.856614,
          lng: 2.3522219,
          zoom: 13
        }
      loadScript('https://reservation.aqin.io/third-party/storage_polyfill/1.0.0/storagePolyfill.min.js', function() {
        if (isSafari) {
          createSessionId()
          options.session_id = getSessionId()
        } else {
          options.session_id = ''
        }
        loadScript('https://maps.googleapis.com/maps/api/js?libraries=places&key=AIzaSyBwF8sRW3cOj38Se0XaNdRYfEVcGfJaJbk', function() {
          loadScript('https://reservation.aqin.io/third-party/pj_jquery/1.11.2/pjQuery.min.js', function() {
            loadScript('https://reservation.aqin.io/third-party/pj_validate/1.10.0/pjQuery.validate.min.js', function() {
              loadScript('https://reservation.aqin.io/third-party/pj_bootstrap/3.3.2/pjQuery.bootstrap.min.js', function() {
                loadScript('https://reservation.aqin.io/third-party/pj_bootstrap_datetimepicker/4.17.37/moment-with-locales.min.js', function() {
                  loadScript('https://reservation.aqin.io/third-party/pj_bootstrap_datetimepicker/4.17.37/pjQuery.bootstrap-datetimepicker.min.js', function() {
                    loadScript('https://reservation.aqin.io/app/web/js/pjFront.js', function() {
                      TaxiBooking = TaxiBooking(options)
                    })
                  })
                })
              })
            })
          })
        })
      })
    })()
  }
}
</script>

<template>
  <Hero
    class="car-hero"
    size="fullheight"
    mask="slant"
  >
    <template #body>
      <div class="columns is-vcentered">
        <div class="column is-7">
          <div class="hero-form-container">
            <div class="car-container-inner is-active">
              <Title
                tag="h2"
                :size="4"
                weight="semi"
              >
                Need a Ride?
              </Title>
              <div id="pjWrapperTaxiBooking_theme6">
                <div id="pjTbsContainer_3301" class="container-fluid"></div>
                <div class="modal fade pjTbModal" id="pjNcbTermModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel"
                     aria-hidden="true">
                  <div class="modal-dialog">
                    <div class="modal-content">
                      <div class="modal-header">
                        <button type="button" class="close" data-dismiss="modal"><span aria-hidden="true">&times;</span><span
                          class="sr-only">Close</span></button>
                        <h4 class="modal-title pjTbModalTitle" id="myModalLabel">Terms and conditions</h4></div>
                      <div class="modal-body"></div>
                      <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="modal fade pjTbModal" id="pjTbsEarlierModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel"
                     aria-hidden="true">
                  <div class="modal-dialog">
                    <div class="modal-content">
                      <div class="modal-header">
                        <button type="button" class="close" data-dismiss="modal"><span aria-hidden="true">&times;</span><span
                          class="sr-only">Close</span></button>
                        <h4 class="modal-title pjTbModalTitle" id="myModalLabel">Date time for accepted enquiries</h4></div>
                      <div class="modal-body"> Your enquiry can be accepted with 2 hour(s) earlier.</div>
                      <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="modal fade pjTbModal" id="pjCssLoginModal" tabindex="-1" role="dialog" aria-labelledby="loginModalLabel"
                     aria-hidden="true">
                  <div class="modal-dialog">
                    <form id="pjCssLoginForm_3301" action="" method="post"><input type="hidden" name="lbs_login" value="1" />
                      <div class="modal-content">
                        <div class="modal-header">
                          <button type="button" class="close" data-dismiss="modal"><span aria-hidden="true">&times;</span><span
                            class="sr-only">Close</span></button>
                          <h4 class="modal-title pjCssModalTitle" id="loginModalLabel">Connexion</h4></div>
                        <div class="modal-body">
                          <div class="row">
                            <div class="col-sm-6">
                              <div class="form-group"><label>Email <span>*</span></label><input type="text" name="login_email"
                                                                                                class="form-control email required"
                                                                                                data-msg-required="This field is required."
                                                                                                data-msg-email="Email is invalid.">
                                <div class="help-block with-errors">
                                  <ul class="list-unstyled"></ul>
                                </div>
                              </div>
                            </div>
                            <div class="col-sm-6">
                              <div class="form-group"><label>Password <span>*</span></label><input type="password"
                                                                                                   name="login_password"
                                                                                                   class="form-control required"
                                                                                                   data-msg-required="This field is required.">
                                <div class="help-block with-errors">
                                  <ul class="list-unstyled"></ul>
                                </div>
                              </div>
                            </div>
                          </div>
                          <div class="row">
                            <div class="col-sm-12">
                              <div class="form-group"><a href="#" class="pjCssLinkForgotPassword">Forgot password?</a></div>
                            </div>
                          </div>
                          <div class="row" style="display: none;">
                            <div class="col-sm-12">
                              <div id="pjLoginMessage_3301" class="form-group text-danger"></div>
                            </div>
                          </div>
                        </div>
                        <div class="modal-footer">
                          <button type="submit" class="btn btn-primary">Connexion</button>
                          <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                        </div>
                      </div>
                    </form>
                  </div>
                </div>
                <div class="modal fade pjTbModal" id="pjCssForgotModal" tabindex="-1" role="dialog" aria-labelledby="forgotModalLabel"
                     aria-hidden="true">
                  <div class="modal-dialog">
                    <form id="pjCssForgotForm_3301" action="" method="post"><input type="hidden" name="lbs_forgot" value="1" />
                      <div class="modal-content">
                        <div class="modal-header">
                          <button type="button" class="close" data-dismiss="modal"><span aria-hidden="true">&times;</span><span
                            class="sr-only">Close</span></button>
                          <h4 class="modal-title pjCssModalTitle" id="forgotModalLabel">Forgot password?</h4></div>
                        <div class="modal-body">
                          <div class="row">
                            <div class="col-sm-12">
                              <div class="form-group"><label>Email <span>*</span></label><input type="text" name="email"
                                                                                                class="form-control email required"
                                                                                                data-msg-required="This field is required."
                                                                                                data-msg-email="Email is invalid.">
                                <div class="help-block with-errors">
                                  <ul class="list-unstyled"></ul>
                                </div>
                              </div>
                            </div>
                          </div>
                          <div class="row">
                            <div class="col-sm-12">
                              <div class="form-group"><a href="#" class="pjCssLinkLogin">Login</a></div>
                            </div>
                          </div>
                          <div class="row" style="display: none;">
                            <div class="col-sm-12">
                              <div id="pjForgotMessage_3301" class="form-group"></div>
                            </div>
                          </div>
                        </div>
                        <div class="modal-footer">
                          <button type="submit" class="btn btn-primary">Send</button>
                          <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                        </div>
                      </div>
                    </form>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="column is-7">
          <div class="car-hero-composition mt-6">
            <img
              class="main-image"
              src="/assets/illustrations/hero/car-hero-left.png"
              alt="Car hero image"
              width="1000"
              height="857"
            >
            <img
              class="left-image"
              :class="active"
              src="/assets/illustrations/hero/car-hero-left.png"
              alt="Car hero image"
              width="1000"
              height="857"
            >
            <img
              class="right-image"
              :class="active"
              src="/assets/illustrations/hero/car-hero-right.png"
              alt="Car hero image"
              width="1000"
              height="857"
            >
          </div>
        </div>
      </div>
    </template>
  </Hero>
</template>

<style lang="scss" scoped>
.car-hero-composition {
  position: relative;

  .main-image {
    opacity: 0;
    pointer-events: none;
  }

  .left-image,
  .right-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
  }

  .right-image {
    z-index: 0;

    &.is-active {
      transform: translate(-44px, -40px);
    }

    transition: all 0.55s ease-out;
  }

  .left-image {
    top: -4rem;
    z-index: 1;

    &.is-active {
      transform: translate(44px, 44px);
    }

    transition: all 0.55s ease-out;
  }
}

.hero-form-container {
  position: relative;

  .hero-form {
    background: var(--card-bg-color);
    border: 1px solid var(--card-border-color);
    box-shadow: var(--light-box-shadow);
    border-radius: 1rem;
    padding: 2.5rem;
    width: 100%;
    max-width: 420px;
    margin: 0 auto;
  }
}

@media only screen and (width <= 767px) {
  .car-hero {
    text-align: center;

    :deep(.title) {
      &.is-2 {
        font-size: 2rem;
      }
    }

    .buttons {
      justify-content: center;
    }
  }

  .hero-form-container {
    margin-top: 3rem;
  }
}

@media only screen and (width >= 768px) and (width <= 1024px) and (orientation: portrait) {
  .car-hero {
    text-align: center;

    :deep(.title) {
      font-size: 2.25rem;
      margin-left: auto;
      margin-right: auto;
      max-width: 580px;
    }

    :deep(.subtitle) {
      margin-left: auto;
      margin-right: auto;
      max-width: 580px;
    }

    .buttons {
      justify-content: center;
    }
  }

  .hero-form-container {
    margin-top: 3rem;
  }
}
</style>
