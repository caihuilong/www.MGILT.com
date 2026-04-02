---
name: "image-analyzer"
description: "Analyzes and describes images uploaded by users. Invoke when user shares screenshots, photos, or visual content and wants analysis or description."
---

# Image Analyzer

Analyzes images uploaded by users to understand their content and provide helpful descriptions.

## When to Use

Invoke this skill when:
- User uploads/shares a screenshot
- User asks to analyze an image
- User provides visual content for review
- User shares error messages shown in browser or application
- User wants to describe what's in an image

## Capabilities

- **Visual Content Analysis**: Describe what appears in the image
- **Error Detection**: Identify error messages, warnings, or issues shown
- **UI/UX Review**: Analyze interface elements, layout, or design
- **Screenshot Interpretation**: Understand context from screenshots
- **Problem Identification**: Spot issues or anomalies in visuals

## How to Use

When invoked:

1. **Receive Image**: Get the image URL or data from user
2. **Analyze Content**: Use available tools to fetch and analyze the image
3. **Provide Description**: Describe what you see in the image
4. **Identify Issues**: Note any errors, problems, or concerns
5. **Offer Solutions**: If issues found, suggest fixes

## Analysis Framework

When analyzing screenshots or UI images, look for:

- **Layout Issues**: Missing elements, broken layout, misalignment
- **Error Messages**: Red text, error icons, warning indicators
- **Visual Quality**: Rendering issues, missing graphics, styling problems
- **Interactive Elements**: Buttons, forms, menus that may be broken
- **Content**: Text that's visible or missing, incorrect information

## Example Analysis

```
Image Analysis Results:
✓ Visual Elements: Navigation bar, hero section, content area
✓ Color Scheme: Uses sage green (#7A9E7E) as primary accent
⚠ Issue Detected: Error message "Module not found" visible
✓ Layout: Responsive design appears intact

Recommended Action: Check if Three.js library loaded correctly.
```

## Best Practices

- Be specific about what you observe
- Note exact error messages or warnings
- Suggest concrete actions to fix issues
- Ask clarifying questions if image is unclear
- Provide both positive observations and problem areas
