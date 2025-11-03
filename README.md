# Recycling Locator

A React-based web application to help users find nearby recycling centers in Bengaluru.

## Features

- **Search Functionality**: Filter recycling centers by name
- **Location Information**: View addresses and distances to recycling centers
- **Material Types**: See what materials each center accepts (Paper, Plastic, Glass, Metal, Electronics, Batteries)
- **Responsive Design**: Clean, modern UI with Tailwind CSS
- **Visual Icons**: Lucide React icons for enhanced user experience

## Code

```jsx
import React, { useState } from 'react';
import { MapPin, Search, Recycle } from 'lucide-react';

export default function RecyclingLocator() {
  const [searchQuery, setSearchQuery] = useState('');

  const recyclingCenters = [
    {
      id: 1,
      name: "Green Earth Recycling Center",
      address: "123 Main St, Bengaluru",
      distance: "1.2 km",
      accepts: ["Paper", "Plastic", "Glass", "Metal"]
    },
    {
      id: 2,
      name: "E-Waste Collection Point",
      address: "456 Tech Park, Bengaluru",
      distance: "2.5 km",
      accepts: ["Electronics", "Batteries"]
    }
  ];

  const filteredCenters = recyclingCenters.filter(center => 
    center.name.toLowerCase().includes(searchQuery.toLowerCase())
  );

  return (
    <div className="min-h-screen bg-gradient-to-br from-green-50 to-emerald-100 p-6">
      <div className="max-w-4xl mx-auto">
        <div className="flex items-center gap-3 mb-6">
          <Recycle className="w-8 h-8 text-emerald-600" />
          <h1 className="text-3xl font-bold text-gray-800">Recycling Locator</h1>
        </div>

        <div className="bg-white rounded-lg shadow-md p-4 mb-6">
          <div className="relative">
            <Search className="absolute left-3 top-3 text-gray-400 w-5 h-5" />
            <input
              type="text"
              placeholder="Search recycling centers..."
              className="w-full pl-10 pr-4 py-2 border border-gray-300 rounded-lg"
              value={searchQuery}
              onChange={(e) => setSearchQuery(e.target.value)}
            />
          </div>
        </div>

        <div className="grid gap-4">
          {filteredCenters.map(center => (
            <div key={center.id} className="bg-white rounded-lg shadow-md p-4">
              <h3 className="font-bold text-lg text-gray-800 mb-2">{center.name}</h3>
              <div className="flex items-start gap-2 text-gray-600 mb-3">
                <MapPin className="w-4 h-4 mt-1" />
                <p className="text-sm">{center.address} • {center.distance}</p>
              </div>
              <div className="flex flex-wrap gap-1">
                {center.accepts.map(item => (
                  <span key={item} className="text-xs bg-emerald-100 text-emerald-700 px-2 py-1 rounded">
                    {item}
                  </span>
                ))}
              </div>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}
```

## Dependencies

- React 18+
- lucide-react (for icons)
- Tailwind CSS (for styling)

## Installation

1. Install dependencies:
```bash
npm install react lucide-react
```

2. Ensure Tailwind CSS is configured in your project

3. Import and use the component:
```jsx
import RecyclingLocator from './RecyclingLocator';

function App() {
  return <RecyclingLocator />;
}
```

## Customization

### Adding More Recycling Centers

Edit the `recyclingCenters` array to add more locations:

```javascript
{
  id: 3,
  name: "Your Center Name",
  address: "Your Address, Bengaluru",
  distance: "X.X km",
  accepts: ["Material1", "Material2"]
}
```

### Styling

The component uses Tailwind CSS utility classes. Modify the className properties to customize colors, spacing, and layout.

## Future Enhancements

- Integration with real mapping APIs (Google Maps, Mapbox)
- GPS-based distance calculation
- Filter by material type
- Opening hours display
- Contact information and directions
- User reviews and 
