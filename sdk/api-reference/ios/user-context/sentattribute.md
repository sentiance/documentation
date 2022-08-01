# SENTAttribute

{% hint style="info" %}
This class is part of an [Early Access](../../../appendix/feature-production-readiness.md) feature, and is subject to change in the future.
{% endhint %}

```
@interface SENTAttribute : NSObject <NSSecureCoding, NSCopying>
```

### name

```
@property (nonatomic, strong, nonnull) NSString *name;
```

### value

```
@property (nonatomic, assign) double value;
```

### isEqualTo:

```
- (BOOL)isEqualToAttribute:(SENTAttribute *)attribute;
```
