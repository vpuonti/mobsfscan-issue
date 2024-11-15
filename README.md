# Mobsfscan issue

https://github.com/MobSF/mobsfscan/issues/99

## repro
Expect no warnings, since both lines are ignored.

```
pip install mobsfscan==0.4.4
mobsfscan .

- Pattern Match ████████████████████████████████████████████████████████████ 5798
- Semantic Grep  6

mobsfscan: v0.4.4 | Ajin Abraham | opensecurity.in
╒══════════════╤════════════════════════════════════════════════════════════════════════════════════════════════════════════════╕
│ RULE ID      │ android_kotlin_hardcoded                                                                                       │
├──────────────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ MASVS        │ MSTG-STORAGE-14                                                                                                │
├──────────────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ CWE          │ CWE-798: Use of Hard-coded Credentials                                                                         │
├──────────────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ OWASP-MOBILE │ M9: Reverse Engineering                                                                                        │
├──────────────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ REFERENCE    │ https://github.com/MobSF/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md#storing-a-key---example │
├──────────────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ DESCRIPTION  │ Files may contain hardcoded sensitive information like usernames, passwords, keys etc.                         │
├──────────────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ SEVERITY     │ WARNING                                                                                                        │
├──────────────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ FILES        │ ╒════════════════╤══════════════╕                                                                              │
│              │ │ File           │ bar/test2.kt │                                                                              │
│              │ ├────────────────┼──────────────┤                                                                              │
│              │ │ Match Position │ 11 - 23      │                                                                              │
│              │ ├────────────────┼──────────────┤                                                                              │
│              │ │ Line Number(s) │ 2            │                                                                              │
│              │ ├────────────────┼──────────────┤                                                                              │
│              │ │ Match String   │ key = "bar"  │                                                                              │
│              │ ╘════════════════╧══════════════╛                                                                              │
╘══════════════╧════════════════════════════════════════════════════════════════════════════════════════════════════════════════╛

```

When matching the file with the warning

```
mobsfscan bar/test2.kt
# no warning seen
```