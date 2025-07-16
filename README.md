# EtherealFabric: Streamlining Complex Workflow Management

EtherealFabric is a Python-based framework designed to orchestrate and manage complex computational workflows with ease and flexibility. It provides a robust and extensible platform for defining, executing, and monitoring workflows comprised of independent tasks, dependencies, and data transformations. Unlike rigid, pre-defined workflow engines, EtherealFabric offers a dynamic, code-centric approach, allowing developers to seamlessly integrate existing scripts, tools, and custom logic into their workflows. This makes it particularly well-suited for data science pipelines, machine learning model training, scientific simulations, and other applications involving intricate computational processes.

The core philosophy of EtherealFabric revolves around modularity and reusability. Workflows are constructed from independent, encapsulated "nodes," each representing a distinct task or operation. These nodes can be chained together to form complex dependencies, defining the flow of data and control within the workflow. The framework provides a clear separation of concerns, allowing developers to focus on the logic of individual tasks without being burdened by the complexities of workflow management. EtherealFabric also includes features for error handling, logging, and real-time monitoring, ensuring that workflows are executed reliably and efficiently.

Furthermore, EtherealFabric is designed to be highly adaptable to different computing environments. It can be deployed on a single machine, a cluster of servers, or even a cloud platform, allowing users to scale their workflows as needed. The framework's flexible architecture supports various execution backends, including local processing, distributed computing frameworks (e.g., Dask, Spark), and task queues (e.g., Celery). This versatility ensures that EtherealFabric can be seamlessly integrated into existing infrastructure and adapted to future technological advancements. The goal is to provide a tool that not only simplifies workflow creation but also empowers users to leverage the full potential of their computing resources.

### Key Features

*   **Node-Based Workflow Definition:** Workflows are defined as directed acyclic graphs (DAGs) composed of independent nodes, each representing a specific task. Nodes are Python classes that inherit from a base `Node` class and implement a `run()` method that executes the task's logic.
*   **Dependency Management:** EtherealFabric automatically resolves dependencies between nodes based on their input and output requirements. The framework ensures that nodes are executed in the correct order, guaranteeing that all necessary data is available before a task is started. This is managed through explicit input/output definitions within each Node class.
*   **Data Serialization and Transfer:** The framework supports various data serialization formats (e.g., JSON, Pickle) for transferring data between nodes. This allows users to work with different data types and formats within the same workflow. Users can also implement custom serialization methods for specialized data structures.
*   **Error Handling and Fault Tolerance:** EtherealFabric includes robust error handling mechanisms to gracefully handle exceptions that occur during workflow execution. It allows users to define custom error handlers for individual nodes or the entire workflow. Retry mechanisms are also built-in, allowing failed tasks to be automatically retried.
*   **Real-Time Monitoring and Logging:** The framework provides real-time monitoring capabilities, allowing users to track the progress of their workflows and identify potential issues. Detailed logs are generated for each node, providing valuable insights into the execution process. Metrics are exposed via a simple API for integration with monitoring systems like Prometheus.
*   **Extensible Execution Backends:** EtherealFabric supports multiple execution backends, allowing users to choose the most appropriate environment for their workflows. Supported backends include local processing, distributed computing frameworks (e.g., Dask, Spark), and task queues (e.g., Celery). New backends can be easily added by implementing a simple interface.
*   **API-Driven Workflow Management:** The framework exposes a comprehensive API for programmatically defining, executing, and managing workflows. This allows users to integrate EtherealFabric into their existing applications and automate workflow management tasks.

### Technology Stack

*   **Python 3.7+:** The core programming language of EtherealFabric. It provides the foundation for the framework's architecture and functionality.
*   **NetworkX:** Used for representing and manipulating workflow graphs. NetworkX provides efficient algorithms for dependency resolution and workflow scheduling.
*   **Dask (Optional):** Used for distributed computing, enabling workflows to be scaled across multiple machines. Dask provides a parallel execution engine for executing tasks in parallel.
*   **Celery (Optional):** Used for asynchronous task execution, allowing workflows to be executed in the background. Celery provides a robust task queue for managing asynchronous tasks.
*   **JSON:** Used for data serialization and configuration management. JSON provides a lightweight and human-readable format for representing data.
*   **Logging:** Python's built-in logging module is used for generating detailed logs of workflow execution.

### Installation

1.  **Clone the Repository:**
    

2.  **Create a Virtual Environment (Recommended):**
    

3.  **Install Dependencies:**
    

4.  **Install Optional Dependencies (if needed):**
    *   For Dask support: `pip install dask distributed`
    *   For Celery support: `pip install celery redis` (Redis is required as a Celery broker)

### Configuration

EtherealFabric utilizes environment variables for configuration. The following variables are supported:

*   `ETHEREALFABRIC_LOG_LEVEL`: Sets the logging level (e.g., DEBUG, INFO, WARNING, ERROR, CRITICAL). Default is INFO.
*   `ETHEREALFABRIC_EXECUTION_BACKEND`: Specifies the execution backend to use (e.g., local, dask, celery). Default is local.
*   `ETHEREALFABRIC_CELERY_BROKER_URL`: The URL of the Celery broker (required if using the Celery backend).
*   `ETHEREALFABRIC_CELERY_RESULT_BACKEND`: The URL of the Celery result backend (required if using the Celery backend).

Example:
    export ETHEREALFABRIC_LOG_LEVEL=DEBUG
    export ETHEREALFABRIC_EXECUTION_BACKEND=dask

### Usage

Here's a basic example of how to define and execute a workflow:

class MyNode(Node):
    def __init__(self, input_data):
        super().__init__()
        self.input_data = input_data
        self.outputs = ['output_data']

    def run(self):
        # Perform some computation
        result = self.input_data * 2
        return {'output_data': result}

# Create nodes
node1 = MyNode(input_data=10)
node2 = MyNode(input_data=node1.outputs['output_data'])

# Define dependencies
workflow = Workflow()
workflow.add_node(node1)
workflow.add_node(node2)
workflow.add_dependency(node1, node2)

# Execute the workflow
results = workflow.execute()

For more detailed API documentation and examples, please refer to the `docs/` directory (currently under development).

### Contributing

We welcome contributions to EtherealFabric! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear and concise code with appropriate documentation and tests.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure that all tests pass before submitting the pull request.

### License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/jjfhwang/EtherealFabric/blob/main/LICENSE) file for details.

### Acknowledgements

We would like to thank the open-source community for their contributions to the technologies that EtherealFabric relies upon.