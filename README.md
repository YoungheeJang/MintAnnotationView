MintAnnotationView
==================

UITextViews with name highlight tag like Facebook


Introduction
==
Do you want to make UITextView like Facebook reply input?
It implements annoate(tag) user and show tag rect.
Additional, I maked UITextView for reply list that just show tag rects from annotation tag.

 * Appear tagged user from annotationList(NSArray)
 * Managed annotationList(It able to use write form)
 * Easy customize.
 

![MintAnnotationMemoView](https://raw.githubusercontent.com/soleaf/MintAnnotationView/master/cs_chatview.gif)

![MintAnnotationChatView](https://raw.githubusercontent.com/soleaf/MintAnnotationView/master/sc_chatview.png)

(MintAnnotationChatView)

![MintAnnotationMemoView](https://raw.githubusercontent.com/soleaf/MintAnnotationView/master/cs_memoview.png)

(MintAnnotationChatView)

How to use
==
Clone or Download and show projct. It's very simple.

MintAnnotationChatView
====

1) If you use xib, Put UITextView on view and set class 'MintAnnotationChatView' else make 'MintAnnotationChatView' object and addSubView.
2) SetDelegate

```objective-c
- (void)textViewDidChange:(UITextView *)textView
{
    // Checking User trying to remove MintAnnotationView's annoatation
    [self.annotationView checkTagDeleting];
    
}

- (BOOL)textView:(UITextView *)textView shouldChangeTextInRange:(NSRange)range replacementText:(NSString *)text
{
    // Checking User trying to edit MintAnnotationView's annoatation
    return [self.annotationView checkingEditingTag:textView andRange:range];
    
}
```

3) Add Event anywhere(Ex. UserNameButtons) Make info dictionary include annotation info. And `annotation:`

```objective-c
NSMutableDictionary *info = [[NSMutableDictionary alloc] init];
[info setObject:@"0" forKey:MintAnnotationInfoID];
[info setObject:@"Mary" forKey:MintAnnotationInfoName];
[info setObject:@"Other user Information" forKey:@"others"];
[self.annotationView annotation:info];
```

4) Getting annotation User List. Use it to post server.

```objective-c
self.annotationView.annotationList;
```

5) Or Get Annoation tagged string.

```objective-c
[self.annotationView makeStringWithTag];
```
result
```html
 hello<u id=12>mary</u>!!
```

MintAnnotationMemoView
====

1. If you use xib, Put UITextView on view and set class 'MintAnnotationMemoView' else make 'MintAnnotationMemoView' object and addSubView.
2. Call `setAnnotationWithMemo: `

```objective-c
NSString *firstMemo = @"<u uid=0>Mary</u> hi mary!!. I'm <u uid=1>Cloud</u>.";
[self.memo annotationWithMemo:firstMemo];
```
