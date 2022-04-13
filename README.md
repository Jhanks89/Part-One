<html>
<head>
    <meta charset="utf-8">
    <meta name="description" content="CNIT 133 homework 5">
    <title>CNIT 133 Homework 5 - Arrays</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css">
    <link rel="stylesheet" href="hw5.css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js"></script>
    <script src="https://cdn.jsdelivr.net/jquery.validation/1.16.0/jquery.validate.min.js"></script>
    <script>
        window.onload = function onloadFunction() {
            /* since hills has a different directory structure than my development system,
                set the correct base URL if this page is on hills  */
            if (location.host == "hills.ccsf.edu") {
                var matches = document.querySelectorAll("a[href^='/cnit133']");
                matches.forEach(match => {
                    match.href = match.href.replace('/cnit133', '/~fpacific/cnit133');
                });
            }
        }
    </script>
</head>

<body>
    <div class="jumbotron text-center banner m-0 p-0">
        <h2 class="centerme title_font">CNIT 133 Homework 5 - Arrays</h2>
    </div>
    <!-- responsive Bootstrap 4 navbar with dropdown and sticky-top behavior -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark sticky-top">
        <div class="container ml-1">
            <a href="/cnit133/">Home</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mx-auto">
                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownLbl" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                            Parts
                        </a>
                        <div class="dropdown-menu w-auto shadow p-0" id="navbarDropdown" aria-labelledby="navbarDropdownLbl">
                            <a class="dropdown-item d-flex flex-nowrap align-items-center px-0 py-3" href="index.html">
                                <div class="flex-shrink-1 text-center px-3"></div>
                                <div class="pl-0 pr-4">
                                    <h6 class="mb-0">Part 1</h6>
                                </div>
                            </a>
                            <a class="dropdown-item d-flex flex-nowrap align-items-center px-0 py-3" href="part2.html">
                                <div class="flex-shrink-1 text-center  px-3"></div>
                                <div class="pl-0 pr-4">
                                    <h6 class="mb-0">Part 2</h6>
                                </div>
                            </a>
                            <a class="dropdown-item d-flex flex-nowrap align-items-center px-0 py-3" href="part3.html">
                                <div class="flex-shrink-1 text-center  px-3"></div>
                                <div class="pl-0 pr-4">
                                    <h6 class="mb-0">Part 3</h6>
                                </div>
                            </a>
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
    <!-- end navbar -->
    <div class="gradient_bg pb-4">
        <form id="form1" onsubmit="return handleSubmit()" method="post" action="form_result.php">
        <div class="row">
            <div class="col-sm mt-3 text-center">
                
                    <label for="userName">Enter a username: </label>
                    <input type="text" id="userName" name="userName" placeholder="Username" required oninvalid="this.setCustomValidity('Username is required')" oninput="this.setCustomValidity('')">
                    <span class="error" aria-live="polite"></span>
            </div>
        </div>
        <div class="row flex-sm-row">
            <div class="col-sm-2 ml-auto mt-3 text-center">
                <fieldset id="radio">
                    <legend class="pt-4">Select a color</legend>
                    <div>
                        <input type="radio" id="Black" name="color" value="Black" required />
                        <label for="Black">Black</label>
                    </div>
                    <div>
                        <input type="radio" id="Orange" name="color" value="Orange" required />
                        <label for="Orange">Orange</label>
                    </div>
                    <div>
                        <input type="radio" id="Blue" name="color" value="Blue" required />
                        <label for="Blue">Blue</label>
                    </div>
                </fieldset>
            </div>
            <div class="col-sm-3 mt-3 mr-auto text-center">
                <fieldset id="checkboxes">
                    <legend>Choose your Favorite activity</legend>
                    <div>
                        <input type="checkbox" id="reading a book" name="interests[]" value="reading a book">
                        <label for="reading a book">Reading a book</label>
                    </div>
                    <div>
                        <input type="checkbox" id="playing video games" name="interests[]" value="playing video games">
                        <label for="playing video games">Playing video games</label>
                    </div>
                    <div>
                        <input type="checkbox" id="hiking" name="interests[]" value="hiking">
                        <label for="hiking">Hiking</label>
                    </div>
                    <div>
                        <input type="checkbox" id="napping" name="interests[]" value="napping">
                        <label for="napping">Napping</label>
                    </div>
                    <div>
                        <input type="checkbox" id="cooking" name="interests[]" value="cooking">
                        <label for="cooking">Cooking</label>
                    </div>
                    <!--
                    <div>
                        <input type="checkbox" id="other" name="interest" value="other">
                        <label for="other">Other</label>
                        <input type="text" id="otherValue" name="other">
                    </div>
                    -->
                    <div id="checkboxError" class="error">
                    </div>
                </fieldset>
            </div>
        </div>
        <div class="row">
            <div class="col-sm text-center mx-auto py-0 mt-3">
                <label for="food">Choose a food:</label>
                <select id="food" name="food" required oninvalid="this.setCustomValidity('please choose a food')" oninput="this.setCustomValidity('')">
                    <option value="">--Choose a food--</option>
                    <option value="pizza">Pizza</option>
                    <option value="pasta">Pasta</option>
                    <option value="sushi">Sushi</option>
                    <option value="burgers">Burgers</option>
                    <option value="tacos">Tacos</option>
                    <option value="seafood">Seafood</option>
                    <option value="salad">Salad</option>
                </select>
                <div class="pt-5 pb-2">
                    <button>Submit</button>
                </div>
                
                <pre id="log">
                </pre>
                <script>
                    function handleSubmit() {
                        //var interestsArray = document.forms['form1'].elements['interests[]'];
                        var interests = document.getElementsByName("interests[]");
                        var selectedInterests = [];
                        $('#checkboxError').html(''); // clear any previous error

                        // alternate way of getting selected checkboxes
                        // var selectedInts = Array.from(form1.querySelectorAll('input[name="interests[]"]:checked'));

                        interests.forEach(interest => {
                            if (interest.checked == true) {
                                selectedInterests.push(interest);
                            }
                        });

                        if (selectedInterests.length == 0) {
                            $('#checkboxError').html('Please select at least one interest');
                            return false; // don't refresh page if validation fails, just
                            //   display validation error message
                        }
                        //return false;
                    }
                </script>
            </div>
        </div>
        </form>
    </div>
    <div class="footer py-2 px-4">
        <div class="row">
            <div class="col-sm-4 small font-weight-light text-center">
                <a href="https://getbootstrap.com/"><img style="height:36px" class="centerme float-left" src="../../images/bootstrap.png" alt="Bootstrap Logo"></a>
            </div>
            <div class="col-sm-2 text-center font-weight-light m-auto">
                <a class="centerme" href="mailto:%20fpacific@mail.ccsf.edu?subject=Re:%20CNIT133%20homework%20page" title="send fpacific an e-mail">Contact</a>
            </div>
            <div class="col-sm-3 text-center m-auto">
                <a href="https://validator.w3.org/check?uri=referer"><img style="height:32px" src="../../images/HTML5_sticker.svg" alt="HTML5"></a>
                <a href="https://jigsaw.w3.org/css-validator/check/referer"><img style="height:31px" src="https://jigsaw.w3.org/css-validator/images/vcss" alt="Valid CSS!"></a>
            </div>
        </div>
    </div>
</body>

</html>
