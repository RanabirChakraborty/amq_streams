# amq_streams_kraft

Ansible role to deploy **Apache Kafka in KRaft mode** (Kafka 4.x and Red Hat Streams for Apache Kafka 3.x).

## Features

- Installs Kafka binaries
- Configures KRaft metadata quorum
- Supports roles: broker, controller, **combined**
- Formats metadata storage
- Deploys `server.properties` and `controller.properties`
- Deploys a `systemd` Kafka service
- Validates active listener ports

## Role Variables

| Variable | Description | Default |
|:---------|:------------|:--------|
| `amq_streams_process_role` | Defines the KRaft node type | `"broker,controller"` |
| `amq_streams_cluster_id` | Unique Kafka KRaft metadata cluster ID | `""` |
| `amq_streams_controller_quorum_voters` | Comma-separated controller voter list in the format `<nodeId>@<host>:<port>` | `"1@localhost:9093"` |
| `amq_streams_kraft_log_dirs` | Directory where Kafka stores data logs | `"/var/lib/kafka/kraft"` |
| `amq_streams_kraft_metadata_log_dir` | Directory for KRaft metadata logs | `"/var/lib/kafka/kraft"` |

## Example Playbook

```yaml
- hosts: kafka_nodes
  roles:
    - amq_streams_kraft
```

## License

Apache License v2.0 or later

## Author Information

* [Ranabir Chakraborty](https://github.com/RanabirChakraborty)