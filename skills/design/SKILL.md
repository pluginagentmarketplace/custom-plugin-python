---
name: design-product
description: Create exceptional user experiences, design systems, and lead product development. Use for UI/UX design, design systems, product management, and technical leadership.
---

# Design & Product Management Skill

Build great products through design and strategic thinking.

## Quick Start

Create a design system component in Figma:

**Component Structure:**
1. Base component (Button)
2. Variants: size (sm, md, lg), variant (primary, secondary), state (default, hover, active)
3. Main component with documentation
4. Instance usage in designs

**Design Tokens:**
```json
{
  "colors": {
    "primary": "#0066CC",
    "secondary": "#6C757D",
    "success": "#28A745"
  },
  "typography": {
    "heading-1": {
      "font-size": "32px",
      "font-weight": 700,
      "line-height": 1.2
    }
  },
  "spacing": {
    "xs": "4px",
    "sm": "8px",
    "md": "16px",
    "lg": "24px"
  }
}
```

## Design System Structure

```
design-system/
├── Foundations/
│   ├── Colors
│   ├── Typography
│   ├── Spacing/Grid
│   ├── Icons
│   └── Elevations/Shadows
├── Components/
│   ├── Atoms (Button, Input, Icon)
│   ├── Molecules (Search Bar, Card)
│   ├── Organisms (Header, Navigation)
│   └── Templates
├── Patterns/
│   ├── Forms
│   ├── Navigation
│   ├── Feedback
│   └── Layouts
└── Documentation/
    ├── Usage Guidelines
    ├── Accessibility
    └── Code Examples
```

## UX Research Framework

### 1. User Research
```
Discovery Phase:
- Interviews (5-8 users)
- Surveys (50+ responses)
- Competitive analysis
- User persona creation

Validation Phase:
- Prototype testing
- Usability testing (5 users)
- A/B testing
- Analytics review
```

### 2. User Journey Mapping
```
Touchpoints: Awareness → Consideration → Decision → Action → Retention

Emotions: Frustration → Curiosity → Confidence → Delight → Loyalty

Pain Points: Document friction areas
Opportunities: Identify improvement areas
```

## Product Development Cycle

### Phase 1: Discovery (Weeks 1-2)
- Define problem and opportunity
- Research user needs
- Competitive analysis
- Create user stories

### Phase 2: Design (Weeks 3-6)
- Create wireframes
- Design high-fidelity mockups
- Build interactive prototypes
- User testing and feedback

### Phase 3: Development (Weeks 7-12)
- Frontend implementation
- Backend development
- Integration testing
- Performance optimization

### Phase 4: Launch (Week 13+)
- Gradual rollout
- Monitor metrics
- Gather user feedback
- Iterate based on data

## Product Metrics & OKRs

**OKR Example:**
```
Objective: Increase user engagement
  Key Result 1: 40% increase in daily active users
  Key Result 2: 25% increase in session duration
  Key Result 3: 60% feature adoption rate
```

**Key Metrics:**
- **DAU/MAU**: Daily/Monthly Active Users
- **Retention**: Day 1, Day 7, Day 30 retention
- **Engagement**: Session duration, feature usage
- **NPS**: Net Promoter Score
- **Churn Rate**: Users leaving per month
- **ARPU**: Average Revenue Per User

## Accessibility Checklist

✅ **WCAG 2.1 Level AA Compliance**
- Color contrast: 4.5:1 for text
- Focus indicators visible
- Keyboard navigation possible
- Screen reader compatible
- Captions for videos
- Alt text for images
- Semantic HTML
- Proper heading hierarchy

## Design Tools & Software

- **Figma**: Collaborative design tool
- **Adobe XD**: Prototyping tool
- **Storybook**: Component library
- **Zeroheight**: Living documentation
- **Hotjar**: User feedback tool
- **Mixpanel**: Analytics
- **UserTesting**: Qualitative research

## Testing & Validation

### Usability Testing
```
Plan → Recruit → Prepare → Conduct → Analyze → Iterate

Sample size: 5-8 users (qualitative)
Duration: 30-60 minutes per session
Goals: Identify friction points
Outputs: Insights and recommendations
```

### A/B Testing
```python
# Variant A vs Variant B
sample_size = 5000  # per variant
duration = 2  # weeks
confidence_level = 0.95
min_effect_size = 0.05  # 5% difference

# Results interpretation
if p_value < 0.05:
    print("Statistically significant")
```

## Product Roadmap Example

**Q1 2025: Foundation**
- Core features v1.0
- Beta user signup
- Initial documentation

**Q2 2025: Growth**
- Feature expansion
- Performance optimization
- Marketing campaign

**Q3 2025: Scale**
- Enterprise features
- Integration partnerships
- Global launch

## QA Testing Strategy

### Test Types
1. **Unit Testing**: Individual components
2. **Integration Testing**: Component interactions
3. **System Testing**: Full application
4. **UAT**: User acceptance testing
5. **Performance Testing**: Load testing
6. **Security Testing**: Vulnerability scanning

### Test Automation
```javascript
// Example with React Testing Library
import { render, screen, fireEvent } from '@testing-library/react';
import { Button } from './Button';

test('button click handler', () => {
  const handleClick = jest.fn();
  render(<Button onClick={handleClick}>Click me</Button>);

  fireEvent.click(screen.getByText('Click me'));
  expect(handleClick).toHaveBeenCalledTimes(1);
});
```

## Learning Resources

- [Nielsen Norman Group](https://www.nngroup.com)
- [Interaction Design Foundation](https://www.interaction-design.org)
- [Design.dev](https://design.dev)
- [The Design of Everyday Things](https://mitpress.mit.edu/9780262525671/)
- [Figma Design System Course](https://www.figma.com/design-systems/)

## Career Progression

**IC Path**: Designer → Senior Designer → Design Lead → Principal Designer
**Manager Path**: Designer → Design Manager → Design Director → VP Design
**Product Path**: PM → Senior PM → Group PM → VP Product

## Communication Templates

**Design Brief:**
- Problem statement
- Target audience
- Success metrics
- Timeline
- Constraints

**Feedback Framework:**
- What works well
- What could improve
- Specific suggestions
- Priority level
