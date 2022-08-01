---
description: Class describing the Authenticated User Information
---

# SENTUserInfo

### userId

```objectivec
@property (nonatomic, strong, readonly) NSString *userId;
```

### token

```objectivec
@property (nonatomic, strong, readonly) SENTToken *token;
```

### initWithUserId: andToken:

```objectivec
- (instancetype) initWithUserId: (NSString*) userId
                       andToken: (SENTToken*) token NS_DESIGNATED_INITIALIZER;
```
