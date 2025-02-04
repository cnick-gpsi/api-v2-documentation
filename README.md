<div class="jumbotron">
    <h2>API Guide for Developers</h2>
    <p class="lead">
        <img src="/apidocs/images/gpsi_logo_flat.png" alt=""/><br>
        Welcome to the GPS Insight API Guide for Developers! This documentation is designed for people familiar with object-oriented programming concepts. You should also be familiar with GPS Insight capabilities from a user's point of view.
    </p>
</div>

<div class="Getting Started page-header">
    <h3 style="align-content: center">Getting Started</h3>
    <p>An application programming interface (API) specifies how some software components should interact with each other. GPS Insight's API provides a form of communication via XML or JSON coding language to push your fleet’s data from our system to your back-end systems (e.g., ERP, Dispatch, CRM). By using our API you can effortlessly integrate your fleet’s data into your back-end systems to provide transparency into payroll, fuel card transactions, additional documentation, asset management, and more.</p>
    <img src="/apidocs/images/API_process.png">
    <p>The typical process for interacting with our API is broken into three high-level steps. You'll need to: <br>
    <ul>
        <li>
            <a href="#SessionToken">Obtain a Session Token.</a>
        </li>
    </ul>
    <ul>
        <li>
            <a href="#Request">Make a Request.</a>
        </li>
    </ul>    <ul>
    <li>
        <a href="#ProcessResponse">Process a Response.</a>
    </li>
</ul>
    </p>

</div>

<div class="row marketing">
    <ul>
        <h3 id="SessionToken" style="margin-bottom: 10px;">   Obtain a Session Token</h3>
        <p>
            In order to interact with the API, you must obtain a session token. You can obtain a session token through authentication, which can be done in two ways:
        <ul>
            <li>
                <strong>Username/Password:</strong> The Username/Password authentication is the simplest method of retrieving a session token. Use this method if you are developing for internal applications where your password can be kept secret.
                <br>
            </li>
            <li>
                <strong>App Token: </strong>The App Token authentication is the most secure method of retrieving a session token by using an alias for your login credentials. Use this method if you want to avoid passing your login credentials via HTTP requests or sharing your portal credentials with vendors. This limited access can be revoked or changed at any time.
            </li>
            <br>
        </ul>
        <div class="alert alert-danger" role="alert"><strong>Note:</strong> The App Token is not less sensitive than a password because it still provides full access to API functions for that user. Using an API App offers the following benefits: It does not allow access to the Portal site, it can be changed or deactivated by admin users, and app usage can be better tracked.</div>
        Once you have a session token, all subsequent requests will not require authentication while the session token is active. The token will eventually expire (varies from about a day to a week), so you will need to occasionally re-authenticate.
        </p>

        <div>
            <table class="table table-hover table-bordered">
                <tbody>
                <tr data-toggle="collapse" data-target="#userPass">
                    <td><a href="/#/"><strong>To obtain a session token with Username/Password</strong></a></td>
                </tr>

                <tr class="hiddenRow">
                    <div class="collapse" id="userPass" style="text-align: left">
                        <td>
                            <ol>
                                <li value="1">Open a web browser.</li>
                                <li value="2">Copy and paste the following URL into the Address Bar, substituting your Username and Password for the XXXX placeholders: </li>
                            </ol>
                            <p class="listcontinue"><code>https://api.gpsinsight.com/v2/userauth/login?username=XXXX&amp;password=XXXX</code>
                            </p>
                            <p class="listcontinue" style="text-indent: 39px">The following response appears:</p>
                            <p class="listcontinue">
                                <img src="/apidocs/images/0000-00.png" class="MaxWidth100PercentNoThumbnail" />
                            </p>
                            <ol data-mc-continue="true">
                                <li value="3">Copy the Session Token (shown above highlighted in yellow), and paste it into Notepad. You will use this token when you make a request. (See #2.&#160;Make a Request).</li>
                            </ol>
                        </td>
                    </div>
                </tr>
                </tbody>
            </table>
        </div>

        <div>
            <table class="table table-hover table-bordered">
                <tbody>
                <tr data-toggle="collapse" data-target="#appToken">
                    <td><a href="/#/"><strong>To obtain a session token with an App&#160;Token</strong></a></td>
                </tr>

                <tr class="hiddenRow">
                    <div id="appToken" class="collapse" style="text-align: left">
                        <td>
                            <ol>
                                <li value="1">Open a web browser, and log in to <a href="http://portal.gpsinsight.com/" target="_blank">portal.gpsinsight.com</a>.</li>
                                <li value="2">From the Menu&#160;Bar, hover over the <b>Account</b> menu, point to <b>Manage Users</b>, and click <b>Manage&#160;access to api V2 functions</b>.</li>
                            </ol><br>
                            <p class="listcontinue" style="text-indent: 39px">The Manage API Apps page appears.</p>
                            <ol data-mc-continue="true">
                                <li value="3">In the API&#160;Apps List grid, click&#160;<b>API&#160;App</b> next to Create New.</li>
                            </ol>
                            <p class="listcontinue" style="text-indent: 39px">
                                <img src="/apidocs/images/0000-01.png" class="MaxWidth100PercentNoThumbnail" />
                            </p>
                            <ol data-mc-continue="true">
                                <li value="4">In the New&#160;API&#160;App window, enter an&#160;App Name and Description, and click <b>Save API&#160;App</b>.</li>
                            </ol>
                            <p class="listcontinue" style="text-indent: 39px">

                                <img src="/apidocs/images/00-0001.png" class="MaxWidth100PercentNoThumbnail" />

                            </p> <br>
                            <p class="listcontinue" style="text-indent: 39px">A new App Token is generated:</p>
                            <p class="listcontinue" style="text-indent: 39px">
                                <img src="/apidocs/images/00-0002.png" class="MaxWidth100PercentNoThumbnail" />
                            </p>
                            <ol data-mc-continue="true">
                                <li value="5">Copy the App Token (shown above highlighted in yellow), and past it into Notepad. You will use this token when you authenticate.</li>
                                <li value="6">Open a new browser tab.</li>
                                <li value="7">Copy and paste the following URL into the Address Bar, substituting your Username and App&#160;Token for the XXXX placeholders:</li>
                            </ol>
                            <p class="listcontinue"><code>https://api.gpsinsight.com/v2/userauth/login?username=XXXX&amp;app_token=XXXX</code>
                            </p>
                            <p class="listcontinue">The following response appears:</p>
                            <p class="listcontinue">
                                <img src="/apidocs/images/0000-00.png" class="MaxWidth100PercentNoThumbnail" />
                            </p>
                            <ol data-mc-continue="true">
                                <li value="8">Copy the Session Token (shown above highlighted in yellow), and paste it into Notepad. You will use this token when you make a request. (See #2.&#160;Make a Request).</li>
                            </ol>

                        </td>
                    </div>
                </tr>
                </tbody>
            </table>
        </div>


        <h3 id="Request" style="margin-bottom: 10px; margin-top: 15px;">   Make a Request</h3>
        <p>
            Technically, you've already made a request (authentication) that returned a session token. Now, you can make additional requests--this time to return data from your GPS Insight account.<br><br>
            <strong>Request Structure</strong><br>
            Before you can make this request, you must understand the request structure.<br>
        </p>
        <img src="/apidocs/images/request_structure.png"/><br><br>
        <p>Use the table below to understand the parts of the following request structure:</p>
        <div class="well well-sm">
            <p class="code">https://<span style="color: #ea6312; font-weight: bold;">api.gpsinsight.com/v2</span>/<span style="color: #e6b729; font-weight: bold;">vehicle</span>/<span style="color: #9e5e9b; font-weight: bold;">location</span>/<span style="color: #54849a; font-weight: bold;">xml</span>?<span style="color: #6aac90; font-weight: bold;">session_token=abcd1234</span>&amp;<span style="font-weight: bold; color: #808000;">vehicle=truck1</span> <!--[CDATA[ ]]--></p>
        </div>
        <div class="table">
            <table class="table table-hover table-bordered">
                <thead style="background-color: grey;">
                <th>Alert</th>
                <th>Example</th>
                <th>Required</th>
                </thead>
                <tbody>
                <tr>
                    <td><strong>API Endpoint</strong><br>Specifies the API endpoint or URL (followed by the http protocol</td>
                    <td>api.gpsinsight.com/v2</td>
                    <td>x</td>
                </tr>
                <tr>
                    <td><strong>Class</strong><br>Specifies the service or class.</td>
                    <td>vehicle</td>
                    <td>x</td>
                </tr>
                <tr>
                    <td><strong>Method</strong><br>Specifies the method.</td>
                    <td>location</td>
                    <td>x</td>
                </tr>
                <tr>
                    <td><strong>Output Format</strong><br>
                        Specifies the formatting for responses. Available formats include:
                        <ul>
                            <li>json (default): JavaScript Object Notation is the current standard for APIs and Web Services. This is the format used if none is specified.</li>
                            <li>xjson: The head and errors information will be put in a HTTP header labeled X-json. The data section will be put in the HTTP body with no additional structure.</li>
                            <li>xml: A common format for transmission of web services data.</li>
                            <li>text: Output structure will be more human readable. This is good for testing.</li>
                        </ul>
                    </td>
                    <td>xml</td>
                    <td></td>
                </tr>
                <tr>
                    <td><strong>Session Token</strong><br>Specifies the session token obtained from authentication.</td>
                    <td>session_token=abcd1234</td>
                    <td>x</td>
                </tr>
                <tr>
                    <td><strong>Method Parameter(s)</strong><br>Specifies the optional parameter(s) within the method. Separate multiple parameters with an ampersand (&).</td>
                    <td>vehicle=truck1</td>
                    <td></td>
                </tr>
                </tbody>
            </table>
        </div>
        <p><div class="alert alert-danger" role="alert"><strong>Note:</strong> You can also add an optional, user-specified value that is returned in the response header (128 character max) to use for troubleshooting (i.e., reference_tag=request_00342), but it is not a core element of the request structure.</div>
        </p>
        <h3 id="ProcessResponse" style="margin-bottom: 10px; margin-top: 15px;">   Process a Response</h3>

        <p><strong>Response Structure</strong><br>The default response will be structured with a head section with meta data about the request, an optional errors section, and a data section containing the formatted response data:</p>
        <div class="well well-sm">{<br>
            "head": { . . . },<br>
            "errors": [{ . . }],<br>
            "data": [{ . . . }]<br>
            }</div>
        <p>The following table provides an example of the content inside of each section (head, errors, data):</p>
        <div class="table">
            <table class="table table-hover table-bordered">
                <thead style="background-color: grey; text-decoration-color: white;">
                <th>Head Section</th>
                <th>Description</th>
                <th>Example</th>
                </thead>
                <tbody>
                <tr>
                    <td><strong>status</strong></td>
                    <td>OK or ERROR if errors were encountered</td>
                    <td>OK</td>
                </tr>
                <tr>
                    <td><strong>method</strong></td>
                    <td>The method used to produce the response</td>
                    <td>listvehicles</td>
                </tr>
                <tr>
                    <td><strong>context</strong></td>
                    <td>The user_context under which the response was generated</td>
                    <td>customer</td>
                </tr>
                <tr>
                    <td><strong>request_time</strong></td>
                    <td>The server time at the request (in MST)</td>
                    <td>May 21 2014 10:47:38</td>
                </tr>
                <tr>
                    <td><strong>session_start</strong></td>
                    <td>The server time at the start of the current session (in MST)</td>
                    <td>May 21 2014 10:44:47</td>
                </tr>
                <tr>
                    <td><strong>request_count</strong></td>
                    <td>The number of times the request has been issued from the current account</td>
                    <td>1</td>
                </tr>
                </tbody>
                <thead style="background-color: grey">
                <th>Error Section</th>
                <th>Description</th>
                <th>Example</th>
                </thead>
                <tbody>
                <tr>
                    <td><strong>code</strong></td>
                    <td>Usually a standard HTTP error code such as 400, 404, 500, etc.</td>
                    <td>403</td>
                </tr>
                <tr>
                    <td><strong>message</strong></td>
                    <td>The standard HTTP message that accompanies the code. For security purposes we do not provide detailed error logs</td>
                    <td>Forbidden (session does not exist)</td>
                </tr>
                </tbody>
                <thead style="background-color: grey">
                <th colspan="3">Data Section</th>
                </thead>
                <tbody>
                <td colspan="3">Formatted response varies by method. Refer to the <a href="">API Reference</a> for examples</td>
                </tbody>

            </table>
            <div class="map">
                <h3 class="fa fa-globe fa-2x" style="margin-bottom: 10px; margin-top: 15px;"> Real-World Example</h3>
                <p>
                    How you process the response depends entirely on your purpose for using the API and the programming language in which the interfacing
                    application is written. GPS Insight provides you with the following simple JavaScript example for how you might use the GPS Insight
                    API to display vehicle location information--in this case on a third-party web map that resides outside of the GPS Insight portal
                    (e.g., your company's website).<br><br>
                    <a href="https://api.gpsinsight.com/v2/examples/javascript_example.html">https://api.gpsinsight.com/v2/examples/javascript_example.html<br><br>
                    </a>
                    <img src="/apidocs/images/real_example.png">
                </p>
            </div>
        </div>
    </ul>
</div>
