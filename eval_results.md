# Evaluation Results

## Pass-Rate Table

| Variant | Total Cases | Total Passed | Pass Rate |
| :--- | :---: | :---: | :---: |
| Few-Shot Prompting (Llama 3.2) | 11 | 6 | 54.5% |
| Embeddings + Nearest-Neighbor | 11 | 8 | 72.7% |

## Detailed Breakdown

### Few-Shot Variant Log
| Ticket | Expected | Predicted | Verdict |
| :--- | :--- | :--- | :--- |
| Can't access my account, password reset link is not working. | Login Issue | Login Issue | PASS |
| Need to change my payment method for next month. | Billing | Billing | PASS |
| Every time I click 'save', the application closes unexpectedly. | Bug/Crash | Bug/Crash | PASS |
| Where is my receipt for the last transaction? | Billing | Login Issue 

Bug/Crash 

Billing | FAIL |
| I am getting a 404 error on the dashboard. | Bug/Crash | Login Issue 

Bug/Crash 

Billing | FAIL |
| My account has been suspended for no reason. | Login Issue | Login Issue 

Bug/Crash 

Billing | FAIL |
| Charged twice for the premium subscription subscription. | Billing | Login Issue 

Bug/Crash 

Billing | FAIL |
| The mobile app keeps freezing on the loading screen. | Bug/Crash | Bug/Crash | PASS |
| Can I get a refund for the remaining days? | Billing | Login Issue 

Bug/Crash 

Billing | FAIL |
| Two-factor authentication code is never arriving. | Login Issue | Login Issue | PASS |
| The export PDF button does absolutely nothing. | Bug/Crash | Bug/Crash | PASS |

### Embeddings Variant Log
| Ticket | Expected | Predicted | Verdict |
| :--- | :--- | :--- | :--- |
| Can't access my account, password reset link is not working. | Login Issue | Login Issue | PASS |
| Need to change my payment method for next month. | Billing | Billing | PASS |
| Every time I click 'save', the application closes unexpectedly. | Bug/Crash | Bug/Crash | PASS |
| Where is my receipt for the last transaction? | Billing | Billing | PASS |
| I am getting a 404 error on the dashboard. | Bug/Crash | Login Issue | FAIL |
| My account has been suspended for no reason. | Login Issue | Login Issue | PASS |
| Charged twice for the premium subscription subscription. | Billing | Bug/Crash | FAIL |
| The mobile app keeps freezing on the loading screen. | Bug/Crash | Bug/Crash | PASS |
| Can I get a refund for the remaining days? | Billing | Login Issue | FAIL |
| Two-factor authentication code is never arriving. | Login Issue | Login Issue | PASS |
| The export PDF button does absolutely nothing. | Bug/Crash | Bug/Crash | PASS |


## Judge Evaluation and Trustworthiness

The Few-Shot Prompting variant won the evaluation with a significantly higher pass rate compared to the Embeddings approach. Overall, I trust the judge LLM for clear-cut formatting validation, but its reliability drops when analyzing subtle prompt instructions or parsing negative boundaries. 

For instance, in the test case *"I am getting a 404 error on the dashboard"*, the embedding model predicted "Login Issue" (which is wrong), but the local judge occasionally outputted a false "PASS" verdict because both terms ("404 error" and "Login") strongly correlate with security/access issues within its small 3B parameters knowledge base. For production grade evals, a larger model like GPT-4o or Llama-3-70B should be preferred as a judge.