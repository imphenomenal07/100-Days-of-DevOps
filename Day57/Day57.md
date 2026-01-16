# Day 57: Print Environment Variables

# 1. Create pod deployment file
  $  vi pod.yaml

# 2. Follow official k8s doc to create file with printing env varibales

https://kubernetes.io/docs/tasks/inject-data-application/define-environment-variable-container/

apiVersion: v1
kind: Pod
metadata:
  name: print-greeting
spec:
  containers:
  - name: env-print-demo
    image: bash
    env:
    - name: GREETING
      value: "Warm greetings to"
    - name: HONORIFIC
      value: "The Most Honorable"
    - name: NAME
      value: "Kubernetes"
    - name: MESSAGE
      value: "$(GREETING) $(HONORIFIC) $(NAME)"
    command: ["echo"]
    args: ["$(MESSAGE)"]

#Modify the file as per requirement

# 3. Create pod 
  $  kubectl apply -f pod.yaml

# 4. Now get pods
  $  kubectl get pods

# 5. Print environment varibales with the given command
