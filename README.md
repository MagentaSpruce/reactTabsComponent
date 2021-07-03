# reactTabsProject
This React project consist of a tabbed component which renders information formatted like one would find on a resume.
This project uses data fetched from an API but can easily be configured to handle local data (API// const url = "https://course-api.com/react-tabs-project";)

This project comes with a brief overview of the pertinent React code as follows:

To start the fetch functionality is set up as well as a loading screen which will take place during API calls by using state.
```React
function App() {
  const [loading, setLoading] = useState(true);
  const [jobs, setJobs] = useState([]);
  const [value, setValue] = useState(0);

  const fetchJobs = async () => {
    const response = await fetch(url);
    const newJobs = await response.json();
  };
  
  
  Once the data has been fetched then the value of jobs should bet set (inside of fetchJobs) to the data results instead of the empty array.
  ```React
      setJobs(newJobs);
    setLoading(false);
    ```
    
    
    To ensure the fetchJobs() function renders on page load the useEffect() method is used.
    ```React
      useEffect(() => {
    fetchJobs();
  }, []);
  ```
  
  
  Conditional loading is functionalized.
  ```React
    if (loading)
    return (
      <section className="section loading">
        <h1>loading...</h1>
      </section>
    );
    ```
    
    
    Now that the data has been retreived it can be displayed. To do this it must first be destructured for use.
    ```React
      const { company, dates, duties, title } = jobs[value];
      ```
      
      Now the return is built.
      ```React
       return (
    <section className="section">
      <div className="title">
        <h2>experience</h2>
        <div className="underline"></div>
      </div>
      <div className="jobs-center">
        </div>
        {/*job info*/}
        <article className="job-info">
          <h3>{title}</h3>
          <h4>{company}</h4>
          <p class="job-date">{dates}</p>
          {duties.map((duty, index) => {
            return (
              <div key={index} class="job-desc">
                <FaAngleDoubleRight className="job-icon" />
                <p>{duties}</p>
              </div>
            );
          })}
        </article>
      </div>
    </section>
  );
}
      
    
    This renders the first item. Now buttons need to be added for each job inside the data array. Once the button is clicked, the state value should change and a different job should display on the list.
    ```React
     <div className="btn-container">
          {jobs.map((item, index) => {
            return (
              <button
                key={item.id}>
                {item.company}
              </button>
            );
          })}
        </div>
        
        
        Now the onClick functionality is set up to change the value to match the index the moment of click.
        ```React
                    return (
              <button
                key={item.id}
                onClick={() => setValue(index)}
              >
                {item.company}
              </button>
            );
            ```
            
            To add an active class to the buttons a conditional statement is used.
            ```React
              <button
                key={item.id}
                onClick={() => setValue(index)}
                className={`job-btn ${index === value && "active-btn"}`}
              >
              ```
              
              Finally the content is rendered to the screen.
              ```React
              ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```


***Finish walkthrough
              
            
        
    
    
  
