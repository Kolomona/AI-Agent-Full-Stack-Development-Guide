# UI/UX Specification

*Design guidance and user experience specifications for frontend implementation. This file bridges the gap between product vision and technical implementation, ensuring frontend teams have clear design direction.*

> **Note for Human Readers**: Throughout this document, `@` symbols are used before filename references (e.g., `@API_CONTRACT.md`) to help AI agents better understand file relationships and importance. These `@` symbols are **not part of the actual filenames** - they are only used in this documentation for AI interpretability. Actual filenames do not have `@` prefixes.

---

## Design Philosophy

### AI Design Limitations & Solutions
**Challenge**: AI cannot create original, innovative design without human guidance.
**Solution**: Use design references, patterns, and templates to guide AI implementation.

### Design Generation Strategies
1. **Design References**: "Like [App Name] but for [specific use case]"
2. **Template Patterns**: "Use [template type] for [app type]"
3. **Component Libraries**: "Use [library] with [style] approach"
4. **Design Systems**: "Follow [design system] patterns"

---

## Design Reference Framework

### How to Specify Design References
When creating this specification, use the format:
```
Design Reference: [App/Website] + [Specific Aspect] + [Customization]
```

**Examples:**
- "Like Spotify's playlist interface but for recipe collections"
- "Use GitHub's issue tracking UI but for task management"
- "Follow Material Design 3 patterns with custom color scheme"
- "Use Notion's block-based editor for content creation"

### Design Reference Categories

#### **Navigation & Layout**
- **Top Navigation**: Like GitHub, with user menu and search
- **Sidebar Navigation**: Like Notion, collapsible with icons
- **Bottom Navigation**: Like Instagram, for mobile-first apps
- **Dashboard Layout**: Like Figma, with sidebar and main content area

#### **Data Display**
- **Card Layouts**: Like Pinterest, responsive grid with hover effects
- **Table Views**: Like Airtable, sortable with inline editing
- **List Views**: Like Slack, with avatars and status indicators
- **Grid Views**: Like Spotify, with cover images and metadata

#### **Forms & Inputs**
- **Form Design**: Like Linear, clean with floating labels
- **Search Interface**: Like Google, with autocomplete and filters
- **File Upload**: Like Dropbox, drag-and-drop with progress
- **Rich Text**: Like Notion, block-based with formatting toolbar

#### **User Feedback**
- **Loading States**: Like Linear, skeleton screens with animations
- **Error Handling**: Like Stripe, contextual with helpful messages
- **Success States**: Like Slack, subtle notifications with actions
- **Empty States**: Like Figma, encouraging with clear next steps

---

## UI/UX Specification Template

### 1. Design System Foundation

#### **Color Palette**
```css
/* Primary Colors */
--primary-50: #f0f9ff;
--primary-500: #3b82f6;
--primary-900: #1e3a8a;

/* Neutral Colors */
--gray-50: #f9fafb;
--gray-500: #6b7280;
--gray-900: #111827;

/* Semantic Colors */
--success: #10b981;
--warning: #f59e0b;
--error: #ef4444;
```

#### **Typography**
```css
/* Font Stack */
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;

/* Scale */
--text-xs: 0.75rem;
--text-sm: 0.875rem;
--text-base: 1rem;
--text-lg: 1.125rem;
--text-xl: 1.25rem;
--text-2xl: 1.5rem;
```

#### **Spacing System**
```css
/* Spacing Scale */
--space-1: 0.25rem;
--space-2: 0.5rem;
--space-4: 1rem;
--space-6: 1.5rem;
--space-8: 2rem;
--space-12: 3rem;
--space-16: 4rem;
```

### 2. Component Specifications

#### **Button Components**
```typescript
// Primary Button
<Button variant="primary" size="md">
  Create Recipe
</Button>

// Secondary Button
<Button variant="secondary" size="sm">
  Cancel
</Button>

// Icon Button
<IconButton variant="ghost" size="sm">
  <PlusIcon />
</IconButton>
```

#### **Form Components**
```typescript
// Text Input
<Input
  label="Recipe Name"
  placeholder="Enter recipe name..."
  error={errors.name}
  required
/>

// Select Dropdown
<Select
  label="Category"
  options={categories}
  value={selectedCategory}
  onChange={handleCategoryChange}
/>

// Textarea
<Textarea
  label="Instructions"
  placeholder="Enter cooking instructions..."
  rows={4}
/>
```

#### **Data Display Components**
```typescript
// Card Component
<Card>
  <CardHeader>
    <CardTitle>Recipe Name</CardTitle>
    <CardSubtitle>Category • 30 min</CardSubtitle>
  </CardHeader>
  <CardContent>
    <p>Recipe description...</p>
  </CardContent>
  <CardFooter>
    <Button>View Recipe</Button>
  </CardFooter>
</Card>

// Table Component
<Table>
  <TableHeader>
    <TableRow>
      <TableHead>Name</TableHead>
      <TableHead>Category</TableHead>
      <TableHead>Actions</TableHead>
    </TableRow>
  </TableHeader>
  <TableBody>
    {recipes.map(recipe => (
      <TableRow key={recipe.id}>
        <TableCell>{recipe.name}</TableCell>
        <TableCell>{recipe.category}</TableCell>
        <TableCell>
          <Button size="sm">Edit</Button>
        </TableCell>
      </TableRow>
    ))}
  </TableBody>
</Table>
```

### 3. Page Layout Specifications

#### **Dashboard Layout**
```typescript
// Main Dashboard Structure
<DashboardLayout>
  <Sidebar>
    <NavigationMenu items={navItems} />
  </Sidebar>
  <MainContent>
    <PageHeader title="Dashboard" />
    <DashboardGrid>
      <StatsCard title="Total Recipes" value={recipeCount} />
      <RecentActivityCard activities={recentActivities} />
      <QuickActionsCard actions={quickActions} />
    </DashboardGrid>
  </MainContent>
</DashboardLayout>
```

#### **Form Pages**
```typescript
// Form Page Structure
<FormPageLayout>
  <PageHeader title="Create Recipe" />
  <FormContainer>
    <FormSection title="Basic Information">
      <Input label="Recipe Name" required />
      <Select label="Category" options={categories} />
      <Textarea label="Description" />
    </FormSection>
    <FormSection title="Ingredients">
      <IngredientList ingredients={ingredients} />
    </FormSection>
    <FormActions>
      <Button variant="secondary">Cancel</Button>
      <Button variant="primary">Save Recipe</Button>
    </FormActions>
  </FormContainer>
</FormPageLayout>
```

### 4. Responsive Design Specifications

#### **Breakpoint System**
```css
/* Mobile First Approach */
--breakpoint-sm: 640px;
--breakpoint-md: 768px;
--breakpoint-lg: 1024px;
--breakpoint-xl: 1280px;
--breakpoint-2xl: 1536px;
```

#### **Responsive Behavior**
- **Mobile (< 768px)**: Single column, bottom navigation, stacked cards
- **Tablet (768px - 1024px)**: Two column layout, side navigation
- **Desktop (> 1024px)**: Multi-column layout, sidebar navigation

### 5. Interaction Patterns

#### **Loading States**
```typescript
// Skeleton Loading
<SkeletonCard>
  <SkeletonTitle />
  <SkeletonText lines={3} />
  <SkeletonButton />
</SkeletonCard>

// Spinner Loading
<LoadingSpinner size="md" />
```

#### **Error States**
```typescript
// Error Boundary
<ErrorBoundary fallback={<ErrorFallback />}>
  <Component />
</ErrorBoundary>

// Form Errors
<Input
  label="Email"
  error="Please enter a valid email address"
/>
```

#### **Success States**
```typescript
// Toast Notifications
<ToastContainer>
  <Toast type="success" message="Recipe saved successfully!" />
</ToastContainer>

// Success Pages
<SuccessPage
  title="Recipe Created!"
  message="Your recipe has been saved and is ready to use."
  actions={[
    { label: "View Recipe", action: viewRecipe },
    { label: "Create Another", action: createAnother }
  ]}
/>
```

### 6. Accessibility Requirements

#### **WCAG 2.1 AA Compliance**
- **Color Contrast**: Minimum 4.5:1 for normal text, 3:1 for large text
- **Keyboard Navigation**: All interactive elements accessible via keyboard
- **Screen Reader Support**: Proper ARIA labels and semantic HTML
- **Focus Management**: Visible focus indicators and logical tab order

#### **Accessibility Patterns**
```typescript
// Accessible Button
<Button
  aria-label="Delete recipe"
  aria-describedby="delete-description"
>
  <TrashIcon />
</Button>

// Accessible Form
<Form>
  <Label htmlFor="recipe-name">Recipe Name</Label>
  <Input
    id="recipe-name"
    aria-describedby="recipe-name-help"
    aria-invalid={hasError}
  />
  <HelpText id="recipe-name-help">
    Enter a descriptive name for your recipe
  </HelpText>
</Form>
```

---

## Design Reference Examples

### **Recipe Management App**
```
Design Reference: Like Notion's database view but for recipe collections
- Use card-based layout for recipe browsing
- Implement drag-and-drop for recipe organization
- Follow Notion's clean, minimal aesthetic
- Use similar color scheme and typography
```

### **Task Management App**
```
Design Reference: Like Linear's issue tracking but for personal tasks
- Use Linear's clean interface and smooth animations
- Implement similar keyboard shortcuts and navigation
- Follow Linear's color-coded priority system
- Use similar empty states and onboarding
```

### **E-commerce Platform**
```
Design Reference: Like Shopify's admin but for small business
- Use Shopify's dashboard layout and navigation
- Implement similar data tables and filtering
- Follow Shopify's form design patterns
- Use similar notification and feedback systems
```

---

## Implementation Guidelines

### **For Frontend AI Agents**
1. **Start with Design Reference**: Use the specified design reference as your foundation
2. **Follow Component Specs**: Implement components exactly as specified
3. **Maintain Consistency**: Use the design system colors, typography, and spacing
4. **Test Responsiveness**: Ensure all components work across breakpoints
5. **Validate Accessibility**: Test with screen readers and keyboard navigation

### **For UI/UX AI Agents**
1. **Analyze Product Vision**: Understand the target users and use cases
2. **Research Design References**: Find appropriate apps/websites to reference
3. **Create Detailed Specs**: Provide specific component and layout specifications
4. **Consider User Flows**: Map out complete user journeys and interactions
5. **Validate with Testing**: Ensure specifications work for target users

### **For Human Project Managers**
1. **Provide Design Direction**: Give specific design references or preferences
2. **Review Mockups**: Approve wireframes before implementation
3. **Test User Experience**: Validate that the design meets user needs
4. **Iterate Based on Feedback**: Refine design based on user testing

---

## File Integration

### **Relationship to Other Files**
- **@ProductVision.md**: Informs design goals and target users
- **@API_CONTRACT.md**: Defines data structure for UI components
- **@ProjectStatusBoard.md**: Tracks design-related issues and decisions
- **@FrontEndStatus.md**: Logs UI/UX implementation progress

### **Update Workflow**
1. **UI/UX Agent**: Creates initial specification based on product vision
2. **Human PM**: Reviews and approves design direction
3. **Frontend Agent**: Implements according to specification
4. **AIPM Agent**: Validates implementation against specification
5. **Iteration**: Update specification based on feedback and testing

---

## Success Metrics

### **Design Quality Indicators**
- ✅ Consistent visual design across all components
- ✅ Responsive design works on all target devices
- ✅ Accessibility standards met (WCAG 2.1 AA)
- ✅ User testing validates design decisions
- ✅ Implementation matches specification

### **User Experience Metrics**
- ✅ Task completion rates > 90%
- ✅ Error rates < 5%
- ✅ User satisfaction scores > 4.0/5.0
- ✅ Time to complete key tasks within target range
- ✅ Accessibility compliance verified

---

*This specification should be updated as the project evolves and user feedback is gathered. The goal is to ensure frontend teams have clear, actionable design guidance that results in usable, attractive interfaces.* 