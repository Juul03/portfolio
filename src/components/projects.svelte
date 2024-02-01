<script>
    let myProjectsData;

    let fetchData = async () => {
        try {
            const response = await fetch('/data/my-work-details.json');

            if (response.ok) {
            console.log("We got the projects!");
            const data = await response.json();
            myProjectsData = data; // Store the JSON data in myProjectsData
            console.log("myProjectsData:", myProjectsData);
            } else {
            console.error("Failed to fetch projects:", response.status);
            }
        } catch (error) {
            console.error("Error fetching projects:", error);
        }
    };

    fetchData();
</script>

<section>
    <h2>My Work</h2>

    <section>
        <!-- For each -->
    </section>
</section>