
# Task 3 — Idempotence

## Test results

| Request | Status code | Number of devices after request |
|---|---:|---:|
| POST probe (first) | 201 | 6 |
| POST probe (second) | 201 | 7 |
| GET probe | 200 | 7 |
| PUT attic (first) | 200 | 7 |
| PUT attic (second) | 200 | 7 |
| DELETE fridge (first) | 200 | 6 |
| DELETE fridge (second) | 404 | 6 |

## Questions

### 1. Is POST idempotent?

No. Sending the same POST request twice creates two devices with the same name. The number of devices increases each time.

### 2. Is PUT idempotent?

Yes. Sending the same PUT request multiple times replaces the device with the same information. The final device data remains unchanged.

### 3. Is DELETE idempotent?

Yes. The first DELETE removes the device. Sending the request again does not change the device list, even though the second request returns a 404 error.
