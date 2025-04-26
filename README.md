import { useState } from 'react'; import { Button } from "@/components/ui/button"; import { Card, CardContent } from "@/components/ui/card";

export default function Home() { const [language, setLanguage] = useState("en"); const [bricksQty, setBricksQty] = useState(0);

const getBrickRate = (qty) => (qty >= 1000 ? 9.5 : 10);

return ( <div className="min-h-screen bg-neutral-900 text-white px-6 py-10 font-sans"> <header className="text-center mb-12"> <h1 className="text-4xl font-bold mb-2">Buniyaad Traders</h1> <p className="text-lg italic text-neutral-400"> {language === "en" ? "Providing strength and quality since 2003." : "2003 se aapke liye mazbooti aur quality supply kar rahe hain."} </p> <div className="mt-4"> <Button variant="secondary" onClick={() => setLanguage(language === "en" ? "hi" : "en")}> {language === "en" ? "Switch to Hinglish" : "Switch to English"} </Button> </div> </header>

<section className="max-w-3xl mx-auto mb-12">
    <Card className="bg-neutral-800 text-white">
      <CardContent className="p-6">
        <h2 className="text-2xl font-semibold mb-4">
          {language === "en" ? "Fly Ash Bricks" : "Fly Ash Bricks (Eet)"}
        </h2>
        <div className="flex items-center gap-4 mb-2">
          <label htmlFor="qty">{language === "en" ? "Quantity" : "Qty (Kitni Eet)"}:</label>
          <input
            type="number"
            id="qty"
            value={bricksQty}
            onChange={(e) => setBricksQty(Number(e.target.value))}
            className="bg-neutral-700 p-2 rounded w-28"
          />
        </div>
        <p>
          {language === "en"
            ? `Rate per brick: ₹${getBrickRate(bricksQty)}`
            : `Har eet ka rate: ₹${getBrickRate(bricksQty)}`}
        </p>
      </CardContent>
    </Card>
  </section>

  <footer className="text-center mt-12 text-sm text-neutral-500">
    <p>Sant Savta Marg, Tandel Chowk, Mazgaon, Mumbai - 400010</p>
    <p>
      {language === "en"
        ? "Transport ₹300/trip (only on Cement, Chemicals & NOGS)"
        : "Transport ₹300/trip sirf Cement, Chemical aur NOGS pe hai."}
    </p>
    <p className="mt-2">
      {language === "en"
        ? "For credit terms (15–30 days), please call to discuss."
        : "Credit (15–30 din) ke liye hume call karke baat karein."}
    </p>
  </footer>

  <a
    href="https://wa.me/919999999999"
    className="fixed bottom-4 right-4 bg-green-500 text-white px-4 py-2 rounded-full shadow-lg hover:bg-green-600 transition"
    target="_blank"
  >
    WhatsApp
  </a>
</div>

); }

