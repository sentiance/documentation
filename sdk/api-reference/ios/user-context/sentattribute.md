# SENTAttribute

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
