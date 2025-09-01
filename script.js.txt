// Sample Dummy Job Data
const jobs = [
  {
    company: "Tata Motors",
    title: "Graduate Engineer Trainee",
    location: "Pune, Maharashtra",
    salary: "₹5.5 LPA",
    reviews: "⭐ 4.2/5 (1200 reviews)"
  },
  {
    company: "Mahindra & Mahindra",
    title: "Design Engineer",
    location: "Chennai, Tamil Nadu",
    salary: "₹6.0 LPA",
    reviews: "⭐ 4.0/5 (900 reviews)"
  },
  {
    company: "Maruti Suzuki",
    title: "Production Engineer",
    location: "Gurgaon, Haryana",
    salary: "₹4.8 LPA",
    reviews: "⭐ 4.3/5 (1500 reviews)"
  },
  {
    company: "Ashok Leyland",
    title: "Quality Engineer",
    location: "Chennai, Tamil Nadu",
    salary: "₹5.2 LPA",
    reviews: "⭐ 3.9/5 (600 reviews)"
  }
];

// Function to render jobs on the page
function renderJobs(filter = "") {
  const jobList = document.getElementById("job-list");
  jobList.innerHTML = ""; // Clear old results

  const filteredJobs = jobs.filter(
    (job) =>
      job.company.toLowerCase().includes(filter.toLowerCase()) ||
      job.title.toLowerCase().includes(filter.toLowerCase()) ||
      job.location.toLowerCase().includes(filter.toLowerCase())
  );

  if (filteredJobs.length === 0) {
    jobList.innerHTML = "<p>No jobs found for your search.</p>";
    return;
  }

  filteredJobs.forEach((job) => {
    const jobCard = document.createElement("div");
    jobCard.classList.add("job-card");

    jobCard.innerHTML = `
      <h3>${job.title}</h3>
      <p><strong>Company:</strong> ${job.company}</p>
      <p><strong>Location:</strong> ${job.location}</p>
      <p><strong>Salary:</strong> ${job.salary}</p>
      <p><strong>Reviews:</strong> ${job.reviews}</p>
    `;

    jobList.appendChild(jobCard);
  });
}

// Search functionality
document.getElementById("search-btn").addEventListener("click", () => {
  const searchInput = doc
