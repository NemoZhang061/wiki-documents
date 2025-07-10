import DocumentList from '@site/src/components/DocumentList';
import Link from '@docusaurus/Link';
import useBaseUrl from '@docusaurus/useBaseUrl';

# Welcome

Welcome onboard **CamThink Wiki Center**！

We’re excited to have you join our community, the best place for you to learn about and explore edge AI technology. We hope that you'll find useful resources and support here, no matter you're a beginner or an experienced developer.

## CamThink, Fueling Imagination to Edge Intelligence

**CamThink** is a brand that provides developers with a variety of **open-architecture hardware** and **open-source software**. We are committed to building an **edge AI perception suite** that can be widely used in the real world. Our focus is on providing multi-dimensional perception capabilities such as visual, audio and environmental data, aiming to allow AI to understand the world more comprehensively and promote the popularization and development of edge intelligence technology. As a sub-brand of Milesight, CamThink inherits its strong R&D capabilities and global support network, providing a strong guarantee for product reliability and continuous innovation.

## Quick Start
To help you get started quickly, here are some links to important resources:
{/* product card container */}
<div className="product-card-container">

  {/* NeoEdge NG4500 series product card */}
  <div className="product-card">
    <div className="product-header">
      <img src={useBaseUrl('img/Overview/NG45xx/NG45XX.png')} alt="NeoEdge NG45XX" className="product-image"/>
      <h3 className="product-title">NeoEdge NG4500 Edge AI Computing Box</h3>
    </div>
    <p className="product-description">
      High-performance edge computing device based on NVIDIA® Jetson platform, suitable for complex AI reasoning and multi-modal data processing scenarios.
    </p>
    <div className="product-links">
      <Link to={useBaseUrl('docs/NeoEdge NG4500 Series/Overview')} className="link-item">
        <span className="link-icon">📖</span>
        <span>product overview</span>
      </Link>
      <Link to={useBaseUrl('docs/NeoEdge NG4500 Series/Quick Start')} className="link-item">
        <span className="link-icon">🚀</span>
        <span>quick start</span>
      </Link>
      <Link to={useBaseUrl('docs/NeoEdge NG4500 Series/NG4500-CB01 Development Board/Dev Guide')} className="link-item">
        <span className="link-icon">🔧</span>
        <span>dev. guide</span>
      </Link>
      <Link to={useBaseUrl('docs/NeoEdge NG4500 Series/Application Guide/Deepseek-r1')} className="link-item">
        <span className="link-icon">📱</span>
        <span>application guide</span>
      </Link>
    </div>
  </div>

  {/* NeoEyes NE101 series product card */}
  <div className="product-card">
    <div className="product-header">
      <img src={useBaseUrl('img/Overview/NE101/NE101.png')} alt="NeoEyes NE101" className="product-image"/>
      <h3 className="product-title">NeoEyes NE101 Low Power Consumption Camera</h3>
    </div>
    <p className="product-description">
      A lightweight vision AI camera that supports image analysis on the edge and wireless connectivity, and is suitable for IoT and lightweight edge AI application scenarios.
    </p>
    <div className="product-links">
      <Link to={useBaseUrl('docs/NeoEyes NE101 Series/Overview')} className="link-item">
        <span className="link-icon">📖</span>
        <span>product overview</span>
      </Link>
      <Link to={useBaseUrl('docs/NeoEyes NE101 Series/Quick Start')} className="link-item">
        <span className="link-icon">🚀</span>
        <span>quick start</span>
      </Link>
      <Link to={useBaseUrl('docs/NeoEyes NE101 Series/NE100-MB01 Development Board/Dev Guide')} className="link-item">
        <span className="link-icon">🔧</span>
        <span>dev. guide</span>
      </Link>
      <Link to={useBaseUrl('docs/NeoEyes NE101 Series/Application Guide/low-power-image-acquisition')} className="link-item">
        <span className="link-icon">📱</span>
        <span>application guide</span>
      </Link>
    </div>
  </div>

</div>

{/* product card template */}
<style>
{`
  .product-card-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 24px;
    margin-bottom: 48px;
  }
  
  .product-card {
    border: 1px solid var(--ifm-border-color);
    border-radius: 12px;
    padding: 24px;
    box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  
  .product-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
  }
  
  .product-header {
    display: flex;
    align-items: center;
    margin-bottom: 16px;
    gap: 16px;
  }
  
  .product-image {
    width: 150px;
    height: 150px;
    object-fit: contain;
    border-radius: 8px;
    padding: 8px;
  }
  
  .product-title {
    margin: 0;
    font-size: 1.5rem;
    font-weight: 600;
  }
  
  .product-description {
    margin: 0 0 16px 0;
    line-height: 1.5;
  }
  
  .product-links {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  
  .link-item {
    display: flex;
    align-items: center;
    padding: 10px 12px;
    border-radius: 6px;
    text-decoration: none;
    transition: background-color 0.2s ease;
  }
  
  .link-item:hover {
    background-color: var(--ifm-hover-overlay);
  }
  
  .link-icon {
    margin-right: 10px;
    font-size: 18px;
  }
  
  @media (max-width: 768px) {
    .product-card-container {
      grid-template-columns: 1fr;
    }
  }
`}
</style>
