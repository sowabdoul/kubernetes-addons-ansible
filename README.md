# Kubernetes Addons Ansible
Production-ready Ansible tasks to deploy and operate Kubernetes addons.
Each task installs and configures a specific addon via Helm, with variables exposed for easy customization.

## Addons
| Task | Description |
|------|-------------|
| [monitoring.yml](ansible/tasks/monitoring.yml) | Kube Prometheus Stack, Grafana, Loki, Tempo, Pyroscope, OpenTelemetry |
| [longhorn.yml](ansible/tasks/longhorn.yml) | Distributed block storage with RWO and RWX StorageClasses |
| [velero.yml](ansible/tasks/velero.yml) | Cluster backup and restore with S3 backend and CSI snapshot support |
| [rancher.yml](ansible/tasks/rancher.yml) | Multi-cluster Kubernetes management UI |
| [ingress.yml](ansible/tasks/ingress.yml) | Nginx ingress controller with autoscaling and load balancer support |
| [openstack-cinder-csi.yml](ansible/tasks/openstack-cinder-csi.yml) | OpenStack Cinder CSI driver for persistent volumes |
| [openstack-cloud-controller.yml](ansible/tasks/openstack-cloud-controller.yml) | OpenStack cloud controller manager integration |

## Requirements
- Ansible 2.15+
- A running Kubernetes cluster with admin.conf available at /etc/kubernetes/admin.conf

Install collections :
```bash
ansible-galaxy collection install -r requirements.yml
```

## Usage
1. Copy and configure the inventory file :
```bash
cp ansible/inventories/kubernetes/hosts.ini.example ansible/inventories/kubernetes/hosts.ini
```

2. Update the variables in hosts.ini with your values.

3. Run a specific task :
```bash
ansible-playbook -i ansible/inventories/kubernetes/hosts.ini ansible/tasks/monitoring.yml
```

## Structure
```
.
├── ansible
│   ├── inventories
│   │   └── kubernetes
│   │       └── hosts.ini.example
│   └── tasks
│       ├── ingress.yml
│       ├── longhorn.yml
│       ├── monitoring.yml
│       ├── openstack-cinder-csi.yml
│       ├── openstack-cloud-controller.yml
│       ├── rancher.yml
│       └── velero.yml
├── requirements.yml
└── README.md
```

## Maintainer
[Abdoulaye Sow](https://github.com/sowabdoul)

