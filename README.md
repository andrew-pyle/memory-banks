# Memory Banks

A personal web app to **store** & **search** URLs and descriptions you want to save.

## Install

**TODO**

## Architecture

- HTML view
- CSS styles
- JS application

### HTML

Preexisting HTML view for search form. User browser form submissions, rather than javascript event handler.

```html
<form role="search" method="GET" action="#"></form>
```

Search state is stored in URL as search params, `application/x-www-form-urlencoded`, so URLs can be saved & shared.

### CSS

- Styles preexisting HTML
- Styles classes provided by search results list

### Javascript (3 independent parts)

- Script to hydrate view from state stored in URL search params
- Web component for search results view
- Javascript class providing search functionality, business logic, & data access

#### Shared Types

```typescript
interface Fact {
  badge: string;
  title: string;
  content: string;
  keyValue: [string, string][];
  link: URL;
}
```

#### Javascript Class Interface

```typescript
interface ExternalBrain {
  init(): Promise<void>; // Loads data from internet sources
  search(searchTerm: string): Fact[];
}
```

#### UNDECIDED: Web Component for Search Results View OR `lit-html` component? Shadow DOM?

```typescript
interface {
    properties: {
        status: 'loading' | 'failure' | 'success';
        factsList: Fact[];
    }
}
/**
 * @cssprop --wc-external-brain-badge-bkg - `background` of a fact's badge. Maybe you want to do reverse-text coloring?
 * @cssprop --wc-external-brain-badge-text - `color` of a fact's badge. Maybe you want to do reverse-text coloring?
 */
```
