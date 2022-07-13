# Connection between MongoDB and server.js

- models/JobSource.js

        import mongoose from "mongoose";

        const jobSourceSchema = new mongoose.Schema({
         name: String,
          url: String,
        });

        export const JobSource = mongoose.model("job-source", jobSourceSchema);

- server.js

        const MONGODB_URI222 = "mongodb://localhost/bbc-job-manager";

        mongoose.connect(MONGODB_URI222, (err) => {
         if (err) {
         console.log({
        error: "Cannot connect to MongoDB database.",
          err: `"${err}"`,
         });
          }
        });

        app.get("/job-sources-local", async (req, res) => {
        const jobSources = await JobSource.find();
        res.status(200).json({ message: "fetching data from local", jobSources });
        });

# .env

        MONGODB_URI=mongodb+srv://<databasename>:<passwords>@cluster.aaaa.mongodb.net>@cluster.aaaa.mongodb.net/<databasename>

# JWT Authentication

-
