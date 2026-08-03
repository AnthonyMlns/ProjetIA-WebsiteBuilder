---
name: component-library
description: Bibliothèque de composants réutilisables avec API, états et patterns
---
## Composants accumulés

### UI primitives
| Composant | Props | États |
|-----------|-------|-------|
| Button | variant, size, loading, disabled, icon, asChild | default, hover, focus, active, loading |
| Input | label, error, helperText, type, placeholder | default, focus, error, disabled |
| Select | options, placeholder, error, searchable | default, open, error, disabled |
| Checkbox | label, checked, indeterminate, error | default, hover, checked, disabled |
| Switch | label, checked, disabled | default, checked, disabled |
| Textarea | label, error, rows, maxLength | default, focus, error |
| Modal | open, onClose, title, size, closeOnOverlay | open, closing |
| Toast | type, message, duration, onDismiss | success, error, warning, info |
| Tooltip | content, position, delay | default, visible |
| Badge | variant, size, dot | default, dot, removable |
| Avatar | src, name, size, status | default, loading, error, offline, online |
| Card | children, padding, hoverable | default, hover |
| Skeleton | variant, width, height | animating |
| Spinner | size, color | spinning |
| Empty state | icon, title, description, action | empty |
| Error state | message, retry | error |
| Table | columns, data, loading, sortable, pagination | loading, empty, populated |
| Pagination | current, total, onChange | disabled states |
| Tabs | items, active, onChange | active, inactive, focus |
| Accordion | items, multiple, defaultOpen | open, closed, focus |
| Progress bar | value, max, size, label, animated | determinate, indeterminate |
| Dropdown menu | items, align, trigger | default, open, item-hover, item-focus |
| Breadcrumbs | items, separator | active (current), link, collapsed |

À enrichir après chaque projet avec les nouveaux composants créés.
