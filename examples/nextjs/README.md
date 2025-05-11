// Each panel exported separately

// Admin Panel
export function AdminPanel() {
  return (
    <div className="p-4">
      <h2 className="text-xl font-bold mb-2">Admin Dashboard</h2>
      <ul className="list-disc ml-6 text-sm">
        <li>Manage users and their roles</li>
        <li>Oversee platform sales and commissions</li>
        <li>View analytics and performance metrics</li>
        <li>Manage product categories</li>
        <li>Control site-wide announcements and offers</li>
        <li>Monitor support and AI assistant logs</li>
      </ul>
    </div>
  );
}

// Seller Panel
export function SellerPanel() {
  return (
    <div className="p-4">
      <h2 className="text-xl font-bold mb-2">Seller Panel</h2>
      <ul className="list-disc ml-6 text-sm">
        <li>Upload and manage products</li>
        <li>Track orders and update inventory</li>
        <li>View earnings and payout status</li>
        <li>Promote products with ads</li>
        <li>Respond to customer queries</li>
        <li>Upload product demo videos</li>
      </ul>
    </div>
  );
}

// Delivery Panel
export function DeliveryPanel() {
  return (
    <div className="p-4">
      <h2 className="text-xl font-bold mb-2">Delivery Dashboard</h2>
      <ul className="list-disc ml-6 text-sm">
        <li>View assigned orders</li>
        <li>Update delivery status in real-time</li>
        <li>Access maps and navigation tools</li>
        <li>Get delivery history and performance</li>
        <li>Chat with support and admin</li>
      </ul>
    </div>
  );
}

// User Panel
export function UserPanel({ search, setSearch, cart, addToCart, products }) {
  const filtered = products.filter(p => p.name.toLowerCase().includes(search.toLowerCase()));
  const categories = ["All", "Fashion", "Kitchen", "Accessories", "Home Decor"];

  return (
    <div>
      <div className="flex items-center justify-between mb-4">
        <input
          placeholder="Search for products..."
          value={search}
          onChange={(e) => setSearch(e.target.value)}
          className="w-2/3 p-2 border rounded"
        />
        <span className="ml-4">Cart: {cart.length}</span>
      </div>

      <Tabs defaultValue="All" className="mb-4">
        <TabsList>
          {categories.map(cat => (
            <TabsTrigger key={cat} value={cat}>{cat}</TabsTrigger>
          ))}
        </TabsList>
        {categories.map(category => (
          <TabsContent key={category} value={category}>
            <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
              {filtered
                .filter(p => category === "All" || p.category === category)
                .map((product) => (
                  <Card key={product.id}>
                    <CardContent className="p-2">
                      <img
                        src={product.image}
                        alt={product.name}
                        className="w-full h-40 object-cover rounded-xl mb-2"
                      />
                      <div className="text-lg font-semibold">{product.name}</div>
                      <div className="text-green-600 font-medium mb-2">{product.price}</div>
                      <Button onClick={() => addToCart(product)}>Add to Cart</Button>
                    </CardContent>
                  </Card>
                ))}
            </div>
          </TabsContent>
        ))}
      </Tabs>

      <div className="mt-6">
        <h2 className="text-xl font-bold mb-2">AI Chat Assistant</h2>
        <p className="text-sm mb-4">Ask anything about our products or your order. Our AI will help you instantly!</p>
        <Input placeholder="Ask a question..." className="mb-2" />
        <Button>Send</Button>
      </div>

      <div className="mt-6">
        <h2 className="text-xl font-bold mb-2">Video Messages</h2>
        <p className="text-sm mb-4">Watch product demos and updates via video messages</p>
        <video controls className="w-full rounded-xl">
          <source src="/sample-video.mp4" type="video/mp4" />
          Your browser does not support the video tag.
        </video>
      </div>
    </div>
  );
}

// Gold Panel
export function GoldPanel() {
  return (
    <div className="p-4">
      <h2 className="text-xl font-bold mb-2">Gold Membership Features</h2>
      <ul className="list-disc ml-6 text-sm">
        <li>Free delivery on all products</li>
        <li>Exclusive early access to sales</li>
        <li>Gold badge on your profile</li>
        <li>Special discounts up to 15%</li>
        <li>Access to monthly gold-only deals</li>
        <li>Video product previews</li>
      </ul>
    </div>
  );
}

// Premium Panel
export function PremiumPanel() {
  return (
    <div className="p-4">
      <h2 className="text-xl font-bold mb-2">Premium Membership Features</h2>
      <ul className="list-disc ml-6 text-sm">
        <li>All Gold features included</li>
        <li>24x7 priority customer support</li>
        <li>Premium-only mega sales</li>
        <li>Exclusive premium gift boxes</li>
        <li>Birthday & festival special surprises</li>
        <li>Early access to AI shopping assistant and video help</li>
      </ul>
    </div>
  );
}
 
