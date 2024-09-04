import React, { useState } from 'react';

function App() {
  const [alcoolPrice, setAlcoolPrice] = useState('');
  const [gasolinaPrice, setGasolinaPrice] = useState('');
  const [bestOption, setBestOption] = useState('');

  const handleAlcoolPriceChange = (event) => {
    setAlcoolPrice(event.target.value);
  };

  const handleGasolinaPriceChange = (event) => {
    setGasolinaPrice(event.target.value);
  };

  const calculateBestOption = () => {
    const alcoolPriceValue = parseFloat(alcoolPrice);
    const gasolinaPriceValue = parseFloat(gasolinaPrice);

    if (alcoolPriceValue && gasolinaPriceValue) {
      const ratio = alcoolPriceValue / gasolinaPriceValue;
      if (ratio < 0.7) {
        setBestOption('Álcool');
      } else {
        setBestOption('Gasolina');
      }
    } else {
      setBestOption('Preencha todos os campos');
    }
  };

  return (
    <div className="container">
      <h1>Qual a melhor opção?</h1>
      <div className="input-group">
        <label htmlFor="alcool-price">Alcool (preço por litro):</label>
        <input
          type="number"
          id="alcool-price"
          value={alcoolPrice}
          onChange={handleAlcoolPriceChange}
        />
      </div>
      <div className="input-group">
        <label htmlFor="gasolina-price">Gasolina (preço por litro):</label>
        <input
          type="number"
          id="gasolina-price"
          value={gasolinaPrice}
          onChange={handleGasolinaPriceChange}
        />
      </div>
      <button onClick={calculateBestOption}>Calcular</button>
      <p>A melhor opção é: {bestOption}</p>
    </div>
  );
}

export default App;
