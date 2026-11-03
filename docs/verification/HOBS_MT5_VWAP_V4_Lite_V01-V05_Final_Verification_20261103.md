# HOBS MT5 VWAP V4 Lite — V-01〜V-05 Final Verification Summary

- **Record date:** 2026-11-03
- **Test data date:** 2026-11-02
- **Environment:** MT5 (Axiory), USDJPY_z / M1 unless noted
- **Indicator:** HOBS MT5 VWAP V4 Lite
- **Overall status:** **PASS — V-01〜V-05 verification closed**
- **Scope note:** V-03 date-boundary behavior was verified with the available test data. Verification on the actual seasonal DST transition date remains pending until the next DST change.

## Final results

| Test | Verification area | Result | Evidence / notes |
|---|---|---|---|
| V-01 | Basic function test | **PASS** | Indicator starts normally; VWAP line draws correctly; calculation and updates operate; chart display is correct. |
| V-02 | Numerical verification test | **PASS** | 1,424 USDJPY_z M1 bars; independent calculation matched; 0 errors; all 1,424 target bars compared; maximum error 0. |
| V-03 | DST / date-boundary test | **PASS (scope-qualified)** | Date-boundary VWAP reset behavior verified. MT5 (Axiory) and TradingView (Pepperstone) reset times were nearly identical in the observed interval; post-reset VWAP updates behaved as expected. Actual DST transition-date verification remains pending. |
| V-04 | Real-time update test | **PASS** | Real-time update and M1 bar-transition update OK; volume increase 31; OHLC changes 31; 316 bars compared; failures 0; maximum error 0. |
| V-05 | Reproducibility test | **PASS** | Chart regeneration OK; post-regeneration Buffer0 matched; calculation consistency OK; 1,424 of 1,424 bars matched; maximum error 0. |

## V-03 scope and interpretation

The V-03 retest used real data around the date boundary (2026-11-02, MT5 00:16–00:30 corresponding to TradingView 07:16–07:30, UTC+7 display offset in the comparison). The MT5 and TradingView VWAP reset timing was nearly identical, and both series continued updating after the reset.

Broker feeds differ (MT5 Axiory vs TradingView Pepperstone), so exact OHLC/VWAP equality is not expected. The observed small value differences are treated as potential broker-rate differences, not as evidence of an MT5 calculation defect.

**Pending follow-up:** Verify behavior on the actual DST transition date (seasonal time change) when that date occurs. This pending seasonal check does not invalidate the current V-03 PASS for the tested date-boundary behavior.

## Final judgment

Within the executed verification scope, HOBS MT5 VWAP V4 Lite passed the basic-function, numerical-accuracy, date-boundary behavior, real-time-update, and reproducibility tests. V-01 through V-05 are recorded as **PASS**, and this verification cycle is **CLOSED**.

Future DST transition-date verification is tracked as a scheduled follow-up, not as an open failure in this completed test cycle.
