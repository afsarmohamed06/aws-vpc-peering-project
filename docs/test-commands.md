# Test commands (run from the laptop through the bastion)

```bash
ssh ewb-bastion
ssh ewb-app-a
hostname -I
ping -c 4 10.20.1.10      # Test 01 baseline (fails before routes), Test 02 forward path (after routes)

ssh ewb-app-b
hostname -I
ping -c 4 10.10.2.10      # Test 03 reverse path
```

Controlled failure: remove only the ICMP Echo Request rule (source 10.10.2.10/32) from `ewb-sg-app-b`,
ping from App-A (expect 100% loss), restore the exact rule, ping again (expect 0% loss).
