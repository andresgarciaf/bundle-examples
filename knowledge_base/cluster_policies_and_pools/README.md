# Cluster policies and pools

This Declarative Automation Bundles example defines a cluster policy and an instance pool.
A classic job cluster uses both resources through `${resources...id}` references.
See the [cluster policy documentation](https://docs.databricks.com/dev-tools/bundles/resources.html#cluster_policy).

## Prerequisites

- Databricks CLI v1.20.0 or above
- Permission to create cluster policies and instance pools
- A classic compute workspace (not serverless-only)

## Usage

1. Set the node type for your cloud if the default Azure type does not fit.

   ```bash
   export BUNDLE_VAR_node_type_id=i3.xlarge
   ```

2. Validate the bundle.

   ```bash
   databricks bundle validate
   ```

3. Deploy the bundle.

   ```bash
   databricks bundle deploy
   ```

4. Run the example job.

   ```bash
   databricks bundle run example_job
   ```

5. Remove the deployed resources.

   ```bash
   databricks bundle destroy
   ```

| Resource | Purpose |
| --- | --- |
| `cluster_policies.team_policy` | Limits node type and autotermination (10–60 minutes) |
| `instance_pools.team_pool` | Pool with zero min idle instances |
| `jobs.example_job` | Classic job that uses the policy and pool |
