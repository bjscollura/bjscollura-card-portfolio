<div class="page-container container">
    
    <div class="casestudy">
      <h1>Short Form Case Study: <br/>Designing "Search"</h1>

      <div class="study-specs">
        <p><strong>Summary:</strong> User research told us that <strong>users love the app</strong>, but they often need to <strong>search multiple times to find what they’re really looking for</strong>. We wanted to <strong>make their searches easier</strong>, and <strong>encourage exploration</strong> of the app to find more classes and sessions they enjoy.</p>
        <hr>
        <p><strong>Duration:</strong> February 24 - March 6, 2020</p>
        <p><strong>Who was involved:</strong> Myself and two colleagues</p>
        <p><strong>End product:</strong> A medium-fidelity digital prototype demonstrating all changes, plus all artifacts leading to that prototype</p>
        <p><strong>My primary contribution:</strong> Information Architecture Lead</p>
      </div>

      <!-- <h2>Browse vs Search</h2> -->
      <div class="casestudy-p">
        <p></p>

        <h3 class="casestudy-h">Browse vs Search</h3>
        <p>There is an often-overlooked but important distinction between <strong>browsing</strong> and <strong>searching</strong>. <strong>Browsing</strong> is a means of discovering what there is to search for - it starts with a base knowledge near zero, and builds ideas for the user until they know what they'd like. <strong>Searching</strong> starts from specific knowledge or needs from the user (they already know what they want), and helps them reduce the possibilities until they can find one like they were looking for.</p>
        <figure>
          <img src="/images/mindbody/01a_browse_2.png" alt="The Explore section of our updated design, with a grid of keywords and icons.">
          <figcaption>The "Explore" section of our updated design. Users are given a list of keywords, paired with images, and organized by tab.</figcaption>
        </figure>
        <figure>
          <img src="/images/mindbody/01b_search_2.png" alt="The Search section of our updated design, with search field, location field, and time and date field.">
          <figcaption>The "Search" section of our updated design. The user is prompted to "Start Typing" - this is great if they know what to type, but if not, better go to "Explore" and find out what's even possible!</figcaption>
        </figure>

        <p>Originally, Mindbody blurred the lines between these two approaches - in fact, the Wellness and Beauty tabs on the results pages even <strong>redirected to the browse section</strong> (called "Explore" in the app), rather than to the search results for the term searched for. This was such a jarring and obvious bug, that it showed how infrequently the tabs were even being used as they are currently configured.</p>
        <p>Our research showed that app users' past activities (their history, their favorites), and their preference for certain staff (which cannot be directly searched for at the moment) are the driving factors when Searching on the app. </p>

        <figure>
          <img src="/images/mindbody/02a_broken-search_2.png" alt="A comparison of the old Search Results pages, showing the Wellness tab's radically different 'browse-based' results page.">
          <figcaption>The "Search Results" section of the old design. The tabs don't behave correctly, leading users to err away from exploring results.</figcaption>
        </figure>

        <h3 class="casestudy-h">Organizing Search Results</h3>
        <p>In MindBody's current design, search results are separated into tabs, defining three kinds of results: <strong>Fitness</strong>, <strong>Wellness</strong>, and <strong>Beauty</strong>. Is this helpful? When searching for Pilates or Hair Removal or a Massage, do we need help narrowing down whether it counts as Fitness or Wellness or Beauty? What is "Beauty Yoga", or "Wellness Hair Removal"? While there were some edge cases, we found that overwhelmingly, there was no real utility to be found here.</p>
        <p>However, there was a missing need to follow individual professionals. Yoga instructors may teach three different classes at two separate facilities, and depending on who we are, we may be interested in a particular class, the studio, or the yogi themself. Therefore, separating the results into separate tabs for <strong>Session</strong>, <strong>Business</strong>, and <strong>Staff</strong> will give us that value. We carefully considered these three terms so that they could apply just as naturally to a Yoga Instructor, as to an Acupuncturist or a Tattoo Artist. We were also careful to make sure that the MindBody app already had a concept of a "Business" and "Staff" in the first place, so that results could be displayed this way at all, and that we weren't adding features that couldn't be supported by the backend datastructures.</p>

        <figure>
          <img src="/images/mindbody/03b_search-results_2.png" alt="The Search Results page, with integrated date/time picker and redesigned tabs to filter Sessions, Businesses, or Staff.">
          <figcaption>The "Search Results" section of the new design. There were few times in which narrowing down your search by Fitness, Wellness, or Beauty was helpful, because there are so few activities that would be considered more than one of those.</figcaption>
        </figure>

        <h3 class="casestudy-h">Filtering Results</h3>
        <p>Filtering search results can be fickle. You don't want so many results that you can't find what you need among them, but you don't want to narrow it so much that you leave out results that may have been what you were looking for. This <strong>filtering tends to happen in two places</strong>, too - once when you type in your search terms (narrowing the results to fit those keywords) - and once when the results screen appears, such as how Amazon allows you to filter results by price ranges, brand, and so forth.</p>
        <p>In their current state, MindBody offers two filters in the first step (the search field, and a "distance from current location" selector), and a few on the results page as well, including a date and time picker. We added this date and time picker to the first phase, because our research told us that users knew three general things when they searched - they knew what they wanted to do, and approximately where and when. They can still adjust this on the results page, but this placement allows for more accurate results on the first pass.</p>
        <p>We also enhanced the remaining secondary filters that were in place. Firstly, <strong>no sorting options were previously available</strong>. Users expect to be able to sort on basic properties important to them, like price and rating. Additionally, the <strong>existing filters were too specific</strong>. For instance, why filter on whether the class specifically has "flexible pricing" (an ill-defined term within the app), when the important factor at the root of it is "how expensive is it?" Our filters provide broader applicability, and map better to the features users told us they care about the most.</p>
        

        <figure>
          <img src="/images/mindbody/04_Search-BeforeAfter_2.png" alt="A Before and After showing their old design, and our redesign, of the search page.">
          <figcaption>Search screen, before and after. We kept and extended the translucent box design, added an explicit "map" icon (previously the map would open whenever the text box was active), and designed "Recent" entries to reflect new search categories.</figcaption>
        </figure>
        <figure>
          <img src="/images/mindbody/05_Filters-BeforeAfter_2.png" alt="A Before and After showing their old design, and our redesign, of the filters page.">
          <figcaption>Filters, before and after. "Sort by" options include Price, Rating, Distance, Alphabetical by Staff or Business, and Time (default).</figcaption>
        </figure>
        
        <h3 class="casestudy-h">Final Thoughts</h3>
        <p>MindBody may think of itself (and even brand itself) as a collection of experiences in Fitness, Wellness, and Beauty, but that doesn't mean that it's the best way to define those experiences in all parts of the app. Here, we see that the users already knew the most efficient way to interact with these businesses, but the search structure was making them work around it in inefficient ways. It reminds me of "Desire Paths", those worn-down trails through the grass in a public area where pedestrians have constantly walked in the absence of an intentional paved lane (even when a paved path is indeed nearby). Looking for those trails of browned grass is often the best way to find the most efficient way through the space, and that's precisely where paved paths would be best placed.</p> 
        <p>Here's another important lesson: <strong>Not all design problems come with complaints</strong>. Many users loved the app DESPITE search flaws, and were often willing to completely overlook them because of it. That doesn’t mean they can’t be improved, or that users won’t notice when they have been improved. It simply reminds us that just asking "what are your problems with the app" isn't enough. You must often witness them experience the app, and see them encounter those problems, to know that those problems exist.</p>
      
      </div>
      <figure>
        <img src="/images/mindbody/MB_image.png" alt="The MindBody Logo">
        <figcaption></figcaption>
      </figure>
    </div>




  </div>