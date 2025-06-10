import React, { useState, useEffect, createContext, useContext, useRef, useCallback } from 'react';

// --- LEAFLET.JS & STYLES ---
// This app uses Leaflet for the interactive map. The necessary CSS and JS are now loaded dynamically by the MapDashboard component.

// --- MOCK DATA & TYPES ---
const initialSites = [
    { id: 'site-1', name: 'Berlin Office', type: 'office', lat: 52.5200, lon: 13.4050, primaryAddress: 'Unter den Linden 1, 10117 Berlin, Germany', entityName: 'Enablon GmbH', siteReference: 'DE-BER-01', detailedAddress: 'Unter den Linden 1, 10117 Berlin, Germany', siteManager: 'Anna Müller', area: '2000 sqm', category: 'Office Building', naceCode: 'L68.20', criticality: 2, downtime: 48, headcount: 150, gridDep: 95, onSiteGenDep: 5, waterSource: 'Municipal', revenue: 50000, ppe: 15000, insuredValue: 12000, deductible: 500, usefulLife: 20, climateLosses: 10, adaptCapex: 250, adaptOpex: 50, scope1: 100, scope2Location: 200, scope2Market: 180, scope3: ['Business Travel', 'Employee Commuting'] },
    { id: 'site-2', name: 'Paris Warehouse', type: 'warehouse', lat: 48.8566, lon: 2.3522, primaryAddress: '1 Rue de la Paix, 75002 Paris, France', entityName: 'Enablon S.A.', siteReference: 'FR-PAR-01', detailedAddress: '1 Rue de la Paix, 75002 Paris, France', siteManager: 'Jean-Luc Dubois', area: '15000 sqm', category: 'Logistics', naceCode: 'H52.10', criticality: 1, downtime: 24, headcount: 80, gridDep: 80, onSiteGenDep: 20, waterSource: 'Municipal', revenue: 120000, ppe: 45000, insuredValue: 40000, deductible: 1000, usefulLife: 30, climateLosses: 5, adaptCapex: 500, adaptOpex: 100, scope1: 300, scope2Location: 150, scope2Market: 140, scope3: ['Upstream transportation and distribution'] },
    { id: 'site-3', name: 'Milan Production', type: 'production_site', lat: 45.4642, lon: 9.1900, primaryAddress: 'Via Montenapoleone 8, 20121 Milan, Italy', entityName: 'Enablon Italia', siteReference: 'IT-MIL-01', detailedAddress: 'Via Montenapoleone 8, 20121 Milan, Italy', siteManager: 'Maria Rossi', area: '30000 sqm', category: 'Manufacturing', naceCode: 'C24.10', criticality: 1, downtime: 12, headcount: 500, gridDep: 60, onSiteGenDep: 40, waterSource: 'Surface Water', revenue: 500000, ppe: 250000, insuredValue: 200000, deductible: 5000, usefulLife: 25, climateLosses: 100, adaptCapex: 2000, adaptOpex: 400, scope1: 1500, scope2Location: 800, scope2Market: 750, scope3: ['Purchased Goods and Services', 'Capital Goods'] },
    { id: 'site-4', name: 'Madrid Production', type: 'production_site', lat: 40.4168, lon: -3.7038, primaryAddress: 'Calle de Alcalá 21, 28014 Madrid, Spain', entityName: 'Enablon España', siteReference: 'ES-MAD-01', detailedAddress: 'Calle de Alcalá 21, 28014 Madrid, Spain', siteManager: 'Carlos Fernández', area: '25000 sqm', category: 'Manufacturing', naceCode: 'C10.82', criticality: 2, downtime: 36, headcount: 350, gridDep: 70, onSiteGenDep: 30, waterSource: 'Municipal', revenue: 350000, ppe: 180000, insuredValue: 150000, deductible: 3000, usefulLife: 22, climateLosses: 20, adaptCapex: 1500, adaptOpex: 300, scope1: 1200, scope2Location: 600, scope2Market: 580, scope3: ['Purchased Goods and Services'] },
    { id: 'site-5', name: 'Amsterdam Production', type: 'production_site', lat: 52.3676, lon: 4.9041, primaryAddress: 'Dam 1, 1012 JS Amsterdam, Netherlands', entityName: 'Enablon B.V.', siteReference: 'NL-AMS-01', detailedAddress: 'Dam 1, 1012 JS Amsterdam, Netherlands', siteManager: 'Sanne de Vries', area: '28000 sqm', category: 'Manufacturing', naceCode: 'C20.14', criticality: 1, downtime: 18, headcount: 420, gridDep: 65, onSiteGenDep: 35, waterSource: 'Well Water', revenue: 420000, ppe: 210000, insuredValue: 180000, deductible: 4000, usefulLife: 28, climateLosses: 50, adaptCapex: 1800, adaptOpex: 350, scope1: 1300, scope2Location: 700, scope2Market: 650, scope3: ['Fuel- and energy-related activities'] },
];

const emptySite = {
    id: '', name: '', type: 'office', lat: 0, lon: 0, primaryAddress: '', entityName: '', siteReference: '', detailedAddress: '', siteManager: '', area: '', category: 'Other', naceCode: '', criticality: 3, downtime: 72, headcount: 0, gridDep: 100, onSiteGenDep: 0, waterSource: 'Other', revenue: 0, ppe: 0, insuredValue: 0, deductible: 0, usefulLife: 0, climateLosses: 0, adaptCapex: 0, adaptOpex: 0, scope1: 0, scope2Location: 0, scope2Market: 0, scope3: []
};

// --- GLOBAL STATE (CONTEXT) ---
const SiteContext = createContext(null);

const SiteProvider = ({ children }) => {
    const [sites, setSites] = useState(initialSites);
    const [isModalOpen, setIsModalOpen] = useState(false);
    const [editingSite, setEditingSite] = useState(null);
    const [analysisResults, setAnalysisResults] = useState(null);
    const [isAnalyzing, setIsAnalyzing] = useState(false);

    const openModal = useCallback((site = null) => {
        setEditingSite(site ? { ...site } : { ...emptySite });
        setIsModalOpen(true);
    }, []);

    const closeModal = useCallback(() => {
        setEditingSite(null);
        setIsModalOpen(false);
    }, []);

    const saveSite = useCallback((siteToSave) => {
        setSites(prevSites => {
            if (siteToSave.id) {
                 const existing = prevSites.find(s => s.id === siteToSave.id);
                 if (existing) {
                    return prevSites.map(site => site.id === siteToSave.id ? siteToSave : site);
                 }
            }
            return [...prevSites, { ...siteToSave, id: `site-${Date.now()}` }];
        });
        closeModal();
    }, [closeModal]);
    
    const runAnalysis = useCallback(async (risks, timeHorizons, scenarios) => {
        setIsAnalyzing(true);
        setAnalysisResults(null);

        const prompt = `
            As a climate risk analyst, generate a JSON object representing a physical climate risk assessment.
            The JSON object should have keys for each of the following risks: ${risks.join(', ')}.
            For each risk, the value should be another object with keys for each time horizon: ${timeHorizons.join(', ')}.
            For each time horizon, the value should be an object with keys for each scenario: ${scenarios.join(', ')}.
            The value for each scenario should be a risk score: "green", "yellow", or "red".
            Prioritize 'red' scores for the 'SSP5-8.5' scenario and long-term horizons, and 'green' scores for 'SSP1-2.6' and short-term horizons to reflect realistic climate projections.
            Do not include any commentary, just the raw JSON object.
        `;

        try {
            let chatHistory = [{ role: "user", parts: [{ text: prompt }] }];
            const payload = { contents: chatHistory };
            const apiKey = "";
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;
            const response = await fetch(apiUrl, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(payload) });
            if (!response.ok) throw new Error(`API call failed with status: ${response.status}`);
            const result = await response.json();
            if (result.candidates?.[0]?.content?.parts?.[0]) {
                const textResponse = result.candidates[0].content.parts[0].text;
                const cleanedJsonString = textResponse.replace(/```json/g, '').replace(/```/g, '').trim();
                const parsedResults = JSON.parse(cleanedJsonString);
                setAnalysisResults(parsedResults);
            } else {
                throw new Error("Invalid response structure from API");
            }
        } catch (error) {
            console.error("Error running analysis:", error);
            alert("Failed to run AI analysis. Please check the console for details.");
        } finally {
            setIsAnalyzing(false);
        }
    }, []);

    const value = { sites, saveSite, isModalOpen, editingSite, openModal, closeModal, analysisResults, isAnalyzing, runAnalysis };

    return (
        <SiteContext.Provider value={value}>
            {children}
        </SiteContext.Provider>
    );
};

// --- ICONS (from lucide-react) ---
const Icon = ({ path, className = "w-4 h-4" }) => ( <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d={path} /></svg> );
const getFileTextIconPath = () => "M14.5 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V7.5L14.5 2zM14 2v6h6M16 13H8M16 17H8M10 9H8";
const getZapIconPath = () => "M13 2 3 14h9l-1 8 10-12h-9l1-8z";
const getMapIconPath = () => "M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z";
const getListIconPath = () => "M8 6h13M8 12h13M8 18h13M3 6h.01M3 12h.01M3 18h.01";
const getBarChart2IconPath = () => "M18 20V10M12 20V4M6 20V14";
const getPencilIconPath = () => "M17 3a2.85 2.83 0 1 1 4 4L7.5 20.5 2 22l1.5-5.5Z";
const getFilePlus2IconPath = () => "M4 22h14a2 2 0 0 0 2-2V7.5L14.5 2H6a2 2 0 0 0-2 2v4M14 2v6h6M8 15h6M11 12v6";
const getBuildingIconPath = () => "M4 22h16M2 10l10-7 10 7M6 10v12h4V10h-4zm6 12v-6h4v6h-4z";
const getWarehouseIconPath = () => "M2 22v-6.452a2.333 2.333 0 0 1 1.09-2.02L12 7l8.91 6.528a2.333 2.333 0 0 1 1.09 2.02V22H2zM15 18h-3v-5h3v5zm-5 0h-3v-5h3v5zm12-2h-3v-5h3v5z";
const getFactoryIconPath = () => "M2 22a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V10l-7-5L2 10v12zm5-8v2h2v-2H7zm4 0v2h2v-2h-2zm4 0v2h2v-2h-2zm-8 4v2h2v-2H7zm4 0v2h2v-2h-2zm4 0v2h2v-2h-2z";
const getXIconPath = () => "M18 6 6 18M6 6l12 12";

const FileTextIcon = (props) => <Icon path={getFileTextIconPath()} {...props} />;
const ZapIcon = (props) => <Icon path={getZapIconPath()} {...props} />;
const MapIcon = (props) => <Icon path={getMapIconPath()} {...props} />;
const ListIcon = (props) => <Icon path={getListIconPath()} {...props} />;
const BarChart2Icon = (props) => <Icon path={getBarChart2IconPath()} {...props} />;
const PencilIcon = (props) => <Icon path={getPencilIconPath()} {...props} />;
const FilePlus2Icon = (props) => <Icon path={getFilePlus2IconPath()} {...props} />;
const BuildingIcon = (props) => <Icon path={getBuildingIconPath()} {...props} />;
const WarehouseIcon = (props) => <Icon path={getWarehouseIconPath()} {...props} />;
const FactoryIcon = (props) => <Icon path={getFactoryIconPath()} {...props} />;
const XIcon = (props) => <Icon path={getXIconPath()} {...props} />;

// --- UI COMPONENTS ---
const Card = ({ children, className = "" }) => <div className={`bg-white border border-gray-200 rounded-lg shadow-sm p-6 ${className}`}>{children}</div>;
const Button = ({ children, onClick, variant = 'primary', className = "", disabled = false }) => { const base = "inline-flex items-center justify-center rounded-md text-sm font-medium transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-gray-400 disabled:opacity-50 disabled:pointer-events-none px-4 py-2 gap-2"; const variants = { primary: "bg-blue-600 text-white hover:bg-blue-700", secondary: "bg-gray-100 text-gray-800 hover:bg-gray-200 border border-gray-300", ghost: "hover:bg-gray-100", }; return <button onClick={onClick} className={`${base} ${variants[variant]} ${className}`} disabled={disabled}>{children}</button>; };
const Input = React.forwardRef(({ className, ...props }, ref) => <input className={`flex h-10 w-full rounded-md border border-gray-300 bg-transparent px-3 py-2 text-sm placeholder:text-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50 ${className}`} ref={ref} {...props} />);
const Label = ({ children, htmlFor }) => <label htmlFor={htmlFor} className="text-sm font-medium text-gray-700 mb-1 block">{children}</label>;
const Select = ({ children, className, ...props }) => <select className={`flex h-10 w-full items-center justify-between rounded-md border border-gray-300 bg-white px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 ${className}`} {...props}>{children}</select>;
const Spinner = ({ className = "h-5 w-5" }) => <svg className={`animate-spin ${className}`} xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"><circle className="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" strokeWidth="4"></circle><path className="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path></svg>;

// --- HEADER & NAVIGATION ---
const Header = ({ activeRoute, onNavigate }) => { const navItems = [ { href: '#/', label: 'Map', icon: <MapIcon /> }, { href: '#/sites', label: 'Manage Sites', icon: <ListIcon /> }, { href: '#/global-risk-analysis', label: 'Global Risk Analysis', icon: <BarChart2Icon /> }, ]; return (<header className="bg-white border-b border-gray-200 sticky top-0 z-40"><div className="container mx-auto px-4 sm:px-6 lg:px-8"><div className="flex items-center justify-between h-16"><div className="flex items-center space-x-2"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className="w-8 h-8 text-blue-600"><path d="M17.5 19H9a7 7 0 1 1 6.71-9h1.79a4.5 4.5 0 1 1 0 9Z"/></svg><h1 className="text-xl font-bold text-gray-800">Climate Risks Map</h1></div><nav className="flex space-x-1">{navItems.map(item => <a key={item.href} href={item.href} onClick={() => onNavigate(item.href)} className={`inline-flex items-center gap-2 px-3 py-2 text-sm font-medium rounded-md transition-colors ${activeRoute === item.href ? 'bg-blue-100 text-blue-700' : 'text-gray-600 hover:bg-gray-100 hover:text-gray-900'}`}>{item.icon}{item.label}</a>)}</nav></div></div></header>); };

// --- REUSABLE RISK COMPONENTS ---
const RiskAnalysisPanel = () => {
    const { sites, runAnalysis, isAnalyzing } = useContext(SiteContext);
    const physicalRisks = ['Wildfire', 'Drought', 'Extreme heat', 'Extreme cold', 'Fluvial flood', 'Coastal flood', 'Extreme precipitation'];
    const timeHorizons = ['Short-term (2030)', 'Medium-term (2040)', 'Long-term (2050)'];
    const scenarios = ['SSP1-2.6', 'SSP2-4.5', 'SSP5-8.5'];
    
    return (
        <Card className="h-full flex flex-col">
            <h2 className="text-lg font-semibold text-gray-800 mb-4">Risk Analysis Scope</h2>
            <div className="space-y-4 flex-grow">
                <div><h3 className="text-sm font-semibold text-gray-600 mb-2">Physical Climate Risks</h3><div className="p-3 bg-gray-50 rounded-md text-sm text-gray-700 space-y-1">{physicalRisks.map(r => <p key={r}>{r}</p>)}</div></div>
                <div><h3 className="text-sm font-semibold text-gray-600 mb-2">Time Horizons & Scenarios</h3><div className="p-3 bg-gray-50 rounded-md text-sm text-gray-700 space-y-1">{timeHorizons.map(h => <p key={h}>{h}</p>)}<p className="pt-2 font-medium">Scenarios: {scenarios.join(', ')}</p></div></div>
                <div><h3 className="text-sm font-semibold text-gray-600 mb-2">Portfolio</h3><p className="p-3 bg-gray-50 rounded-md text-sm text-gray-700">{sites.length} sites in scope</p></div>
            </div>
            <Button onClick={() => runAnalysis(physicalRisks, timeHorizons, scenarios)} variant="primary" className="w-full mt-6" disabled={isAnalyzing}>
                {isAnalyzing ? <><Spinner className="-ml-1 mr-3 h-5 w-5 text-white"/>Analyzing...</> : <>✨ Run Group Analysis</>}
            </Button>
        </Card>
    );
};

const RiskMatrix = ({ results, isAnalyzing: loading, from }) => {
    if (loading) { return <div className="flex flex-col items-center justify-center p-8"><Spinner className="h-10 w-10 text-blue-600 mb-4"/><p className="text-gray-600 font-medium">Generating risk matrix...</p></div>; }
    if (!results) { return <div className="text-center py-8 bg-gray-50 rounded-md"><p className="text-gray-500 font-medium">{from === 'map' ? "Run group analysis to generate the portfolio risk matrix." : from === 'global' ? "Go to the 'Map' tab to run a group analysis." : "Run site-specific analysis to generate the risk matrix."}</p></div>; }

    const risks = Object.keys(results);
    const horizons = Object.keys(results[risks[0]] || {});
    const scenarios = Object.keys(results[risks[0]]?.[horizons[0]] || {});
    const scoreColors = { red: 'bg-red-500', yellow: 'bg-yellow-400', green: 'bg-green-500' };

    return (
         <div className="overflow-x-auto"><table className="min-w-full divide-y divide-gray-200 border border-gray-200"><thead className="bg-gray-50"><tr><th scope="col" className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider border-r">Physical Risk</th>{horizons.map(h => <th key={h} scope="col" colSpan={scenarios.length} className="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider border-r">{h}</th>)}</tr><tr><th scope="col" className="px-6 py-3 border-r"></th>{horizons.map(h => scenarios.map(s => <th key={`${h}-${s}`} scope="col" className="px-2 py-2 text-center text-xs font-medium text-gray-500 uppercase tracking-wider border-l border-r">{s.split('-')[0]}</th>))}</tr></thead><tbody className="bg-white divide-y divide-gray-200">{risks.map(risk => (<tr key={risk} className="divide-x divide-gray-200"><td className="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-800">{risk}</td>{horizons.map(h => scenarios.map(s => <td key={`${risk}-${h}-${s}`} className="p-1"><div className={`w-full h-10 flex items-center justify-center rounded ${scoreColors[results[risk][h][s]] || 'bg-gray-200'}`}></div></td>))}</tr>))}</tbody></table></div>
    );
};


// --- PAGES ---
const MapDashboard = () => {
    const mapRef = useRef(null);
    const matrixRef = useRef(null);
    const markersRef = useRef([]);
    const { sites, openModal, isModalOpen, analysisResults, isAnalyzing } = useContext(SiteContext);
    const [isLeafletLoaded, setLeafletLoaded] = useState(false);
    const [isGeneratingReport, setIsGeneratingReport] = useState(false);

    const loadScript = (id, src) => { return new Promise((resolve, reject) => { if (document.getElementById(id)) { resolve(); return; } const script = document.createElement('script'); script.id = id; script.src = src; script.async = true; script.onload = resolve; script.onerror = reject; document.body.appendChild(script); }); };

    useEffect(() => {
        const cssId = 'leaflet-css';
        if (!document.getElementById(cssId)) { const link = document.createElement('link'); link.id = cssId; link.rel = 'stylesheet'; link.href = 'https://unpkg.com/leaflet@1.9.4/dist/leaflet.css'; document.head.appendChild(link); }
        loadScript('leaflet-js', 'https://unpkg.com/leaflet@1.9.4/dist/leaflet.js').then(() => { setLeafletLoaded(true); });
    }, []);

    useEffect(() => {
        if (isLeafletLoaded && window.L && !mapRef.current) { const mapContainer = document.getElementById('map'); if (mapContainer && !mapContainer._leaflet_id) { mapRef.current = window.L.map('map').setView([48.8, 8.5], 4.5); window.L.tileLayer('https://{s}.basemaps.cartocdn.com/rastertiles/voyager/{z}/{x}/{y}{r}.png', { attribution: '&copy; OpenStreetMap &copy; CARTO', maxZoom: 20 }).addTo(mapRef.current); } }
    }, [isLeafletLoaded]);

    useEffect(() => {
        if (!mapRef.current || !isLeafletLoaded) return;
        
        markersRef.current.forEach(marker => marker.remove());
        markersRef.current = [];
        const siteIcons = { office: { path: getBuildingIconPath(), color: 'text-blue-600' }, warehouse: { path: getWarehouseIconPath(), color: 'text-yellow-600' }, production_site: { path: getFactoryIconPath(), color: 'text-red-600' } };

        sites.forEach(site => {
            const iconInfo = siteIcons[site.type]; if (!iconInfo) return;
            const iconHtml = `<div class="p-1.5 bg-white rounded-full shadow-lg border-2 border-white ${iconInfo.color}"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="w-6 h-6"><path d="${iconInfo.path}"></path></svg></div>`;
            const customIcon = window.L.divIcon({ html: iconHtml, className: 'custom-map-icon', iconSize: [40, 40], iconAnchor: [20, 40], popupAnchor: [0, -40] });
            const marker = window.L.marker([site.lat, site.lon], { icon: customIcon }).addTo(mapRef.current);
            marker.on('click', () => openModal(site));
            marker.bindTooltip(`<div class="font-bold text-base text-gray-800">${site.name}</div><div class="capitalize text-sm text-gray-600">${site.type.replace('_', ' ')}</div>`, { offset: [0, -35], direction: 'top' });
            markersRef.current.push(marker);
        });

    }, [sites, openModal, isLeafletLoaded]);
    
    const generateReportNarrative = async (results, section) => {
        if (!results && (section === 'summary' || section === 'adaptation')) return `Cannot generate ${section} because analysis has not been run.`;

        const prompts = {
            summary: `You are a sustainability consultant writing an executive summary for a climate risk report. Based on the following JSON data of the risk analysis, write a 2-paragraph executive summary. The summary should: 1. Start with a clear opening statement about the purpose of the report. 2. Identify the 2-3 highest risks based on the number of "red" scores in the "Long-term (2050)" horizon under the "SSP5-8.5" scenario. 3. Mention that the analysis aligns with regulatory frameworks like IFRS S2 and ESRS E1. 4. Conclude by recommending the development of a strategic adaptation plan. Risk Data: ${JSON.stringify(results, null, 2)} Provide only the text for the executive summary, without any titles or markdown.`,
            adaptation: `You are a climate adaptation strategist. Based on the provided risk analysis, generate a portfolio-level summary of 3 key adaptation strategies. For each strategy, provide a "name" and a "description". Structure your response as a JSON array of objects. Do not include any text outside of the JSON array. Risk Data: ${JSON.stringify(results, null, 2)}`
        };
        const prompt = prompts[section];
        if (!prompt) return `Invalid report section: ${section}`;
        
        try {
            let chatHistory = [{ role: "user", parts: [{ text: prompt }] }];
            const payload = { contents: chatHistory };
            const apiKey = "";
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;
            const response = await fetch(apiUrl, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(payload) });
            if (!response.ok) throw new Error(`API call failed: ${response.status}`);
            const result = await response.json();
            const textResponse = result.candidates?.[0]?.content?.parts?.[0]?.text;
            if (!textResponse) throw new Error("Invalid API response");
            return textResponse;
        } catch (error) {
            console.error(`Error generating report section '${section}':`, error);
            return `An error occurred while generating the AI content for section: ${section}.`;
        }
    };
    
    const handleGenerateReport = async () => {
        setIsGeneratingReport(true);
        try {
            await Promise.all([loadScript('jspdf-js', 'https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js'), loadScript('html2canvas-js', 'https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js')]);
            if (!analysisResults) { alert("Please run an analysis before generating a report."); setIsGeneratingReport(false); return; }
    
            const { jsPDF } = window.jspdf;
            const pdf = new jsPDF('p', 'mm', 'a4');
            const pdfWidth = pdf.internal.pageSize.getWidth();
            const pdfMargin = 15;
            let yPos = pdfMargin;

            // --- PDF CONTENT ---
            pdf.setFontSize(22).setFont('helvetica', 'bold');
            pdf.text('Physical Climate Risk Report', pdfWidth / 2, yPos, { align: 'center' });
            yPos += 15;

            // Company Overview
            pdf.setFontSize(14).setFont('helvetica', 'bold');
            pdf.text('1. Company Overview', pdfMargin, yPos);
            yPos += 7;
            pdf.setFontSize(10).setFont('helvetica', 'normal');
            const companyDesc = "This report details the climate risk assessment for 'Global Corp Inc.', a multinational organization with significant manufacturing and logistics operations across Europe. Our portfolio includes office buildings, warehouses, and production facilities, each with unique operational characteristics and dependencies.";
            const companyLines = pdf.splitTextToSize(companyDesc, pdfWidth - pdfMargin * 2);
            pdf.text(companyLines, pdfMargin, yPos);
            yPos += companyLines.length * 4 + 5;
            pdf.setFont('helvetica', 'bold').text('Sites included in Analysis:', pdfMargin, yPos);
            yPos += 5;
            sites.forEach(site => {
                pdf.setFont('helvetica', 'normal').text(`- ${site.name} (${site.type.replace('_',' ')}) located at ${site.primaryAddress}`, pdfMargin + 2, yPos);
                yPos += 5;
            });
            yPos += 5;
    
            // Executive Summary
            pdf.setFontSize(14).setFont('helvetica', 'bold');
            pdf.text('2. Executive Summary', pdfMargin, yPos);
            yPos += 7;
            const summaryText = await generateReportNarrative(analysisResults, 'summary');
            pdf.setFontSize(10).setFont('helvetica', 'normal');
            const summaryLines = pdf.splitTextToSize(summaryText, pdfWidth - pdfMargin * 2);
            pdf.text(summaryLines, pdfMargin, yPos);
            yPos += summaryLines.length * 4 + 10;
    
            if (yPos > pdf.internal.pageSize.getHeight() - 40) { pdf.addPage(); yPos = pdfMargin; }

            // Map Screenshot
            pdf.setFontSize(14).setFont('helvetica', 'bold');
            pdf.text('3. Portfolio Risk Exposure Map', pdfMargin, yPos);
            yPos += 7;
            const mapEl = document.getElementById('map');
            const mapCanvas = await window.html2canvas(mapEl, { useCORS: true });
            const mapImgData = mapCanvas.toDataURL('image/png');
            const mapHeight = (mapCanvas.height * (pdfWidth - pdfMargin * 2)) / mapCanvas.width;
            pdf.addImage(mapImgData, 'PNG', pdfMargin, yPos, pdfWidth - pdfMargin * 2, mapHeight);
            yPos += mapHeight + 10;
    
            if (yPos > pdf.internal.pageSize.getHeight() - 40) { pdf.addPage(); yPos = pdfMargin; }
    
            // Risk Matrix Image
            pdf.setFontSize(14).setFont('helvetica', 'bold');
            pdf.text('4. Group Level Risk Matrix', pdfMargin, yPos);
            yPos += 7;
            const matrixCanvas = await window.html2canvas(matrixRef.current, { scale: 2 });
            const matrixImgData = matrixCanvas.toDataURL('image/jpeg', 0.9);
            const matrixHeight = (matrixCanvas.height * (pdfWidth - pdfMargin * 2)) / matrixCanvas.width;
            pdf.addImage(matrixImgData, 'JPEG', pdfMargin, yPos, pdfWidth - pdfMargin * 2, matrixHeight);
            yPos += matrixHeight + 10;
    
            if (yPos > pdf.internal.pageSize.getHeight() - 60) { pdf.addPage(); yPos = pdfMargin; }
    
            // Adaptation Actions
            pdf.setFontSize(14).setFont('helvetica', 'bold');
            pdf.text('5. Proposed Climate Adaptation Strategies', pdfMargin, yPos);
            yPos += 7;
            const adaptationText = await generateReportNarrative(analysisResults, 'adaptation');
            const actions = JSON.parse(adaptationText.replace(/```json/g, '').replace(/```/g, '').trim());
            pdf.setFontSize(10);
            actions.forEach(action => {
                pdf.setFont('helvetica', 'bold').text(`- ${action.name}:`, pdfMargin + 2, yPos);
                yPos += 5;
                pdf.setFont('helvetica', 'normal').text(pdf.splitTextToSize(action.description, pdfWidth - pdfMargin * 2 - 2), pdfMargin + 2, yPos);
                yPos += 10;
                if (yPos > pdf.internal.pageSize.getHeight() - 20) { pdf.addPage(); yPos = pdfMargin; }
            });
            yPos += 5;
            
            // Regulatory Mapping
            pdf.setFontSize(14).setFont('helvetica', 'bold');
            pdf.text('6. Regulatory Disclosure Mapping', pdfMargin, yPos);
            yPos += 7;
            pdf.setFontSize(10).setFont('helvetica', 'bold');
            pdf.text('IFRS S2:', pdfMargin, yPos);
            pdf.setFont('helvetica', 'normal');
            pdf.text('The identified risks, scenarios, and financial implications in this report form the basis for disclosures on climate-related risks and opportunities.', pdfMargin + 20, yPos);
            yPos += 7;
            pdf.setFont('helvetica', 'bold');
            pdf.text('ESRS E1:', pdfMargin, yPos);
            pdf.setFont('helvetica', 'normal');
            pdf.text('This analysis supports datapoints E1-1 (adaptation plan), E1-7 (physical risks), and E1-8 (potential financial effects).', pdfMargin + 20, yPos);
    
            pdf.save('Climate_Risk_Report.pdf');
        } catch (error) { console.error("Failed to generate PDF:", error); alert("An error occurred while generating the report. Please check the console."); } finally { setIsGeneratingReport(false); }
    };
    
    return ( <div className="p-6 h-[calc(100vh-64px)] overflow-y-auto"><div className={`grid grid-cols-1 lg:grid-cols-3 gap-6 transition-all duration-300 ease-in-out ${isModalOpen ? 'filter blur-sm brightness-75' : ''}`}><div className="lg:col-span-2 h-[60vh] lg:h-[calc(100vh-120px)] rounded-lg overflow-hidden shadow-md"><div id="map" className="w-full h-full bg-gray-200">{!isLeafletLoaded && <div className="w-full h-full flex items-center justify-center"><p className="text-gray-500 font-medium">Loading Map...</p></div>}</div></div><div className="lg:col-span-1 h-full"><RiskAnalysisPanel /></div></div><div className={`mt-6 transition-all duration-300 ease-in-out ${isModalOpen ? 'filter blur-sm brightness-75' : ''}`}><Card><div ref={matrixRef} className="p-4 bg-white"><h2 className="text-lg font-semibold text-gray-800 mb-2">Group Level Risk Matrix (TCFD/IFRS S2)</h2><RiskMatrix results={analysisResults} isAnalyzing={isAnalyzing} from="map" /></div>{analysisResults && (<div className="pt-4 mt-4 border-t"><Button onClick={handleGenerateReport} disabled={isGeneratingReport || !isLeafletLoaded}>{isGeneratingReport ? <><Spinner className="-ml-1 mr-3"/>Generating Report...</> : <>✨ Generate PDF Report</>}</Button></div>)}</Card></div></div> );
};

const SiteManagementPage = () => { const { sites, openModal } = useContext(SiteContext); const siteTypeDisplay = { office: { label: 'Office', icon: BuildingIcon, color: 'bg-blue-100 text-blue-700' }, warehouse: { label: 'Warehouse', icon: WarehouseIcon, color: 'bg-yellow-100 text-yellow-700' }, production_site: { label: 'Production Site', icon: FactoryIcon, color: 'bg-red-100 text-red-700' } }; return ( <div className="p-6"><Card className="p-4 sm:p-6"><div className="flex flex-col sm:flex-row justify-between items-start sm:items-center mb-4 gap-4"><h1 className="text-2xl font-bold text-gray-900">Site Management</h1><Button onClick={() => openModal()} variant="primary"><FilePlus2Icon />Add New Site</Button></div><div className="overflow-x-auto"><table className="min-w-full divide-y divide-gray-200"><thead className="bg-gray-50"><tr><th scope="col" className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Site Name</th><th scope="col" className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Site Type</th><th scope="col" className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Address</th><th scope="col" className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Coordinates</th><th scope="col" className="relative px-6 py-3"><span className="sr-only">Edit</span></th></tr></thead><tbody className="bg-white divide-y divide-gray-200">{sites.map(site => (<tr key={site.id} className="hover:bg-gray-50"><td className="px-6 py-4 whitespace-nowrap"><div className="text-sm font-medium text-gray-900">{site.name}</div></td><td className="px-6 py-4 whitespace-nowrap"><span className={`px-2 inline-flex text-xs leading-5 font-semibold rounded-full ${siteTypeDisplay[site.type]?.color || 'bg-gray-100 text-gray-800'}`}>{siteTypeDisplay[site.type]?.label || site.type}</span></td><td className="px-6 py-4 whitespace-nowrap text-sm text-gray-600 max-w-xs truncate">{site.primaryAddress}</td><td className="px-6 py-4 whitespace-nowrap text-sm text-gray-600 font-mono">{`${site.lat.toFixed(4)}, ${site.lon.toFixed(4)}`}</td><td className="px-6 py-4 whitespace-nowrap text-right text-sm font-medium"><Button onClick={() => openModal(site)} variant="ghost"><PencilIcon />Edit</Button></td></tr>))}</tbody></table></div></Card></div> ); };

const SiteFormModal = () => {
    const { isModalOpen, closeModal, editingSite, saveSite } = useContext(SiteContext);
    const [activeTab, setActiveTab] = useState('basic');
    const [formData, setFormData] = useState(null);
    const [siteAnalysisResults, setSiteAnalysisResults] = useState(null);
    const [isSiteAnalyzing, setIsSiteAnalyzing] = useState(false);
    const [adaptationPlan, setAdaptationPlan] = useState(null);
    const [isGeneratingPlan, setIsGeneratingPlan] = useState(false);
    
    useEffect(() => { if (isModalOpen && editingSite) { setFormData(editingSite); setActiveTab('basic'); setSiteAnalysisResults(null); setAdaptationPlan(null); } else { setFormData(null); } }, [isModalOpen, editingSite]);

    const handleRunSiteAnalysis = useCallback(async () => {
        setIsSiteAnalyzing(true);
        setSiteAnalysisResults(null);
        const risks = ['Wildfire', 'Drought', 'Extreme heat', 'Extreme cold', 'Fluvial flood', 'Coastal flood', 'Extreme precipitation'];
        const timeHorizons = ['Short-term (2030)', 'Medium-term (2040)', 'Long-term (2050)'];
        const scenarios = ['SSP1-2.6', 'SSP2-4.5', 'SSP5-8.5'];
        const prompt = `As a climate risk analyst, generate a JSON object representing a physical climate risk assessment for a specific site. The site is a "${editingSite.type}" located at "${editingSite.primaryAddress}". The JSON object should have keys for each of the following risks: ${risks.join(', ')}. For each risk, the value should be another object with keys for each time horizon: ${timeHorizons.join(', ')}. For each time horizon, the value should be an object with keys for each scenario: ${scenarios.join(', ')}. The value for each scenario should be a risk score: "green", "yellow", or "red". Given the location, prioritize risks logically (e.g., higher heat/drought risk for Madrid, higher flood risk for Amsterdam). Prioritize 'red' scores for the 'SSP5-8.5' scenario and long-term horizons. Do not include any commentary, just the raw JSON object.`;

        try {
            let chatHistory = [{ role: "user", parts: [{ text: prompt }] }];
            const payload = { contents: chatHistory };
            const apiKey = "";
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;
            const response = await fetch(apiUrl, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(payload) });
            if (!response.ok) throw new Error(`API call failed: ${response.status}`);
            const result = await response.json();
            if (result.candidates?.[0]?.content?.parts?.[0]) {
                const textResponse = result.candidates[0].content.parts[0].text;
                const cleanedJsonString = textResponse.replace(/```json/g, '').replace(/```/g, '').trim();
                const parsedResults = JSON.parse(cleanedJsonString);
                setSiteAnalysisResults(parsedResults);
            } else { throw new Error("Invalid API response structure"); }
        } catch (error) { console.error("Error running site analysis:", error); alert("Failed to run AI site analysis."); } finally { setIsSiteAnalyzing(false); }
    }, [editingSite]);

    const handleGeneratePlan = useCallback(async () => {
        setIsGeneratingPlan(true);
        setAdaptationPlan(null);
        const prompt = `You are a climate adaptation specialist. For a site with the following characteristics: Name: ${editingSite.name}, Type: ${editingSite.type}, Location: ${editingSite.primaryAddress}. This site has the following high-priority risks identified: Wildfire, Extreme heat, Drought. Please generate a JSON array of 3 recommended climate adaptation measures. Each object in the array must have the following keys: "name", "description", "cost", and "applicableRisk". For the "cost", provide a realistic estimated cost range in Euros (e.g., "€50,000 - €100,000"). Provide only the raw JSON array, without any surrounding text or markdown.`;

        try {
            let chatHistory = [{ role: "user", parts: [{ text: prompt }] }];
            const payload = { contents: chatHistory };
            const apiKey = "";
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;
            const response = await fetch(apiUrl, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(payload) });
            if (!response.ok) throw new Error(`API call failed: ${response.status}`);
            const result = await response.json();
            if (result.candidates?.[0]?.content?.parts?.[0]) {
                const textResponse = result.candidates[0].content.parts[0].text;
                const cleanedJsonString = textResponse.replace(/```json/g, '').replace(/```/g, '').trim();
                const parsedPlan = JSON.parse(cleanedJsonString);
                setAdaptationPlan(parsedPlan);
            } else { throw new Error("Invalid API response structure"); }
        } catch (error) { console.error("Error generating adaptation plan:", error); alert("Failed to generate AI adaptation plan."); } finally { setIsGeneratingPlan(false); }
    }, [editingSite]);

    if (!isModalOpen || !formData) return null;

    const handleInputChange = (e) => {
        const { name, value, type, checked } = e.target;
        if (type === 'checkbox') {
            const currentScope3 = formData.scope3 || [];
            if(checked) { setFormData({ ...formData, scope3: [...currentScope3, value] }); } else { setFormData({ ...formData, scope3: currentScope3.filter(item => item !== value) }); }
        } else { setFormData({ ...formData, [name]: type === 'number' ? parseFloat(value) || 0 : value }); }
    };

    const handleSave = (e) => { e.preventDefault(); saveSite(formData); };
    const tabs = [ { id: 'basic', label: 'Basic Info' }, { id: 'characteristics', label: 'Site Characteristics' }, { id: 'operational', label: 'Operational Context' }, { id: 'financial', label: 'Financial & Asset Data' }, { id: 'ghg', label: 'GHG & Energy' }, { id: 'risk', label: 'Risk Analysis' }, { id: 'adaptation', label: 'Climate Adaptation' }];
    const scope3Categories = [ 'Purchased Goods and Services', 'Capital Goods', 'Fuel- and energy-related activities', 'Upstream transportation and distribution', 'Waste generated in operations', 'Business Travel', 'Employee Commuting', 'Upstream leased assets' ];
    
    const renderContent = () => {
        switch (activeTab) {
            case 'adaptation': return (<div><Button onClick={handleGeneratePlan} variant="primary" className="mb-4" disabled={isGeneratingPlan}>{isGeneratingPlan ? <><Spinner className="-ml-1 mr-3 h-5 w-5"/>Generating...</> : <>✨ Generate Action Plan</>}</Button>{isGeneratingPlan && <div className="flex flex-col items-center justify-center p-8"><Spinner className="h-10 w-10 text-blue-600 mb-4"/><p className="text-gray-600 font-medium">Generating adaptation plan...</p></div>}{!isGeneratingPlan && !adaptationPlan && <div className="text-center py-8 bg-gray-50 rounded-md"><p className="text-gray-500 font-medium">Generate an action plan to see suggested climate adaptation measures.</p></div>}{!isGeneratingPlan && adaptationPlan && (<div className="space-y-4"><h3 className="text-md font-semibold text-gray-800">Adaptation Measures</h3>{adaptationPlan.map((measure, index) => (<div key={index} className="p-4 border border-gray-200 rounded-lg"><h4 className="font-bold text-gray-900">{measure.name}</h4><p className="text-sm text-gray-600 mt-1">{measure.description}</p><div className="flex justify-between items-center mt-3"><span className="text-xs font-semibold text-gray-500 bg-gray-100 px-2 py-1 rounded-full">{measure.applicableRisk}</span><span className="text-sm font-bold text-gray-800">{measure.cost}</span></div></div>))}</div>)}</div>);
            case 'risk': return (<div><Button onClick={handleRunSiteAnalysis} variant="primary" className="mb-4" disabled={isSiteAnalyzing}>{isSiteAnalyzing ? <><Spinner className="-ml-1 mr-3 h-5 w-5"/>Analyzing...</> : <>✨ Run Site Analysis</>}</Button><RiskMatrix results={siteAnalysisResults} isAnalyzing={isSiteAnalyzing} from="site" /></div>);
            case 'basic': return <div className="grid grid-cols-1 md:grid-cols-2 gap-4"><div><Label htmlFor="name">Site Name</Label><Input id="name" name="name" value={formData.name} onChange={handleInputChange} /></div><div><Label htmlFor="type">Site Type</Label><Select id="type" name="type" value={formData.type} onChange={handleInputChange}><option value="office">Office</option><option value="warehouse">Warehouse</option><option value="production_site">Production Site</option></Select></div><div><Label htmlFor="lat">Latitude</Label><Input id="lat" name="lat" type="number" value={formData.lat} onChange={handleInputChange} /></div><div><Label htmlFor="lon">Longitude</Label><Input id="lon" name="lon" type="number" value={formData.lon} onChange={handleInputChange} /></div><div className="md:col-span-2"><Label htmlFor="primaryAddress">Primary Address (for map)</Label><Input id="primaryAddress" name="primaryAddress" value={formData.primaryAddress} onChange={handleInputChange} /></div></div>;
            case 'characteristics': return <div className="grid grid-cols-1 md:grid-cols-2 gap-4"><div><Label htmlFor="entityName">Entity Name</Label><Input id="entityName" name="entityName" value={formData.entityName} onChange={handleInputChange} /></div><div><Label htmlFor="siteReference">Site Reference</Label><Input id="siteReference" name="siteReference" value={formData.siteReference} onChange={handleInputChange} /></div><div className="md:col-span-2"><Label htmlFor="detailedAddress">Detailed Address</Label><Input id="detailedAddress" name="detailedAddress" value={formData.detailedAddress} onChange={handleInputChange} /></div><div><Label htmlFor="siteManager">Site Manager</Label><Input id="siteManager" name="siteManager" value={formData.siteManager} onChange={handleInputChange} /></div><div><Label htmlFor="area">Area (e.g., 1000 sqm)</Label><Input id="area" name="area" value={formData.area} onChange={handleInputChange} /></div></div>;
            case 'operational': return <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4"><div><Label htmlFor="category">Site Category</Label><Select id="category" name="category" value={formData.category} onChange={handleInputChange}><option>Data Center</option><option>Manufacturing</option><option>Logistics</option><option>Office Building</option><option>Retail Store</option><option>Other</option></Select></div><div><Label htmlFor="naceCode">NAICS / NACE Code</Label><Select id="naceCode" name="naceCode" value={formData.naceCode} onChange={handleInputChange}><option value="A01">A01</option><option value="C10">C10</option><option value="C20.14">C20.14</option><option value="C24.10">C24.10</option><option value="H52.10">H52.10</option><option value="L68.20">L68.20</option></Select></div><div><Label>Criticality Tier</Label><div className="flex items-center space-x-4 h-10">{[1, 2, 3].map(tier => <label key={tier} className="flex items-center space-x-2"><input type="radio" name="criticality" value={tier} checked={formData.criticality === tier} onChange={handleInputChange} className="h-4 w-4 text-blue-600"/><span>{tier}</span></label>)}</div></div><div><Label htmlFor="downtime">Max Tolerable Downtime (hrs)</Label><Input id="downtime" name="downtime" type="number" value={formData.downtime} onChange={handleInputChange} /></div><div><Label htmlFor="headcount">Headcount on Site</Label><Input id="headcount" name="headcount" type="number" value={formData.headcount} onChange={handleInputChange} /></div><div><Label htmlFor="waterSource">Main Water Source</Label><Select id="waterSource" name="waterSource" value={formData.waterSource} onChange={handleInputChange}><option>Municipal</option><option>Well Water</option><option>Surface Water</option><option>Other</option></Select></div><div><Label>Grid Dependency (%)</Label><Input name="gridDep" type="number" value={formData.gridDep} min="0" max="100" onChange={handleInputChange} /></div><div><Label>On-site Gen Dependency (%)</Label><Input name="onSiteGenDep" type="number" value={formData.onSiteGenDep} min="0" max="100" onChange={handleInputChange} /></div></div>;
            case 'financial': return <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4"><div><Label>Annual Revenue (kEUR)</Label><Input name="revenue" type="number" value={formData.revenue} onChange={handleInputChange} /></div><div><Label>Gross PP&E (kEUR)</Label><Input name="ppe" type="number" value={formData.ppe} onChange={handleInputChange} /></div><div><Label>Insured Value (kEUR)</Label><Input name="insuredValue" type="number" value={formData.insuredValue} onChange={handleInputChange} /></div><div><Label>Deductible (kEUR)</Label><Input name="deductible" type="number" value={formData.deductible} onChange={handleInputChange} /></div><div><Label>Remaining Useful Life (yrs)</Label><Input name="usefulLife" type="number" value={formData.usefulLife} onChange={handleInputChange} /></div><div><Label>Hist. Climate Losses (kEUR)</Label><Input name="climateLosses" type="number" value={formData.climateLosses} onChange={handleInputChange} /></div><div><Label>Adaptation Capex (kEUR)</Label><Input name="adaptCapex" type="number" value={formData.adaptCapex} onChange={handleInputChange} /></div><div><Label>Adaptation Opex (kEUR)</Label><Input name="adaptOpex" type="number" value={formData.adaptOpex} onChange={handleInputChange} /></div></div>;
            case 'ghg': return <div className="grid grid-cols-1 md:grid-cols-2 gap-6"><div><div><Label>Scope 1 (tCO₂e)</Label><Input name="scope1" type="number" value={formData.scope1} onChange={handleInputChange} /></div><div className="mt-4"><Label>Scope 2 – Location (tCO₂e)</Label><Input name="scope2Location" type="number" value={formData.scope2Location} onChange={handleInputChange} /></div><div className="mt-4"><Label>Scope 2 – Market (tCO₂e)</Label><Input name="scope2Market" type="number" value={formData.scope2Market} onChange={handleInputChange} /></div></div><div><Label>Material Scope 3 Categories</Label><div className="p-4 border rounded-md max-h-60 overflow-y-auto space-y-2">{scope3Categories.map(cat => <label key={cat} className="flex items-center space-x-3"><input type="checkbox" value={cat} checked={formData.scope3?.includes(cat)} onChange={handleInputChange} className="h-4 w-4 rounded" /><span>{cat}</span></label>)}</div></div></div>;
            default: return null;
        }
    };

    return (
        <div className="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-50 transition-opacity"><form onSubmit={handleSave} className="bg-white rounded-lg shadow-2xl w-full max-w-4xl h-[90vh] flex flex-col m-4"><div className="flex justify-between items-center p-4 border-b"><h2 className="text-xl font-bold text-gray-800">{editingSite?.id.startsWith('site-') ? 'Edit Site' : 'Add New Site'}</h2><Button onClick={closeModal} variant="ghost" className="p-2 -mr-2"><XIcon /></Button></div><div className="border-b border-gray-200"><nav className="-mb-px flex space-x-4 px-4 overflow-x-auto" aria-label="Tabs">{tabs.map(tab => <button key={tab.id} type="button" onClick={() => setActiveTab(tab.id)} className={`whitespace-nowrap py-3 px-1 border-b-2 font-medium text-sm ${activeTab === tab.id ? 'border-blue-500 text-blue-600' : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300'}`}>{tab.label}</button>)}</nav></div><div className="p-6 overflow-y-auto flex-grow">{renderContent()}</div><div className="flex justify-end items-center p-4 border-t bg-gray-50 rounded-b-lg"><div className="flex gap-2"><Button type="button" onClick={closeModal} variant="secondary">Cancel</Button><Button type="submit" variant="primary">Save Changes</Button></div></div></form></div>
    );
};

const GlobalRiskAnalysisPage = () => { const { analysisResults, isAnalyzing } = useContext(SiteContext); return ( <div className="p-6"><Card><h1 className="text-2xl font-bold text-gray-900 mb-2">Global Risk Analysis</h1><p className="text-sm text-gray-600 mb-6">This matrix shows the aggregated physical climate risk for the entire site portfolio. To generate or update the matrix, run a new analysis from the 'Map' tab.</p><RiskMatrix results={analysisResults} isAnalyzing={isAnalyzing} from="global" /></Card></div> ); };

// --- MAIN APP COMPONENT ---
export default function App() {
    const [route, setRoute] = useState(window.location.hash || '#/');
    const handleNavigate = useCallback((path) => { window.location.hash = path; }, []);
    useEffect(() => { const handleHashChange = () => setRoute(window.location.hash || '#/'); window.addEventListener('hashchange', handleHashChange); return () => window.removeEventListener('hashchange', handleHashChange); }, []);
    const renderPage = () => { switch (route) { case '#/sites': return <SiteManagementPage />; case '#/global-risk-analysis': return <GlobalRiskAnalysisPage />; case '#/': default: return <MapDashboard />; } };

    return (
        <SiteProvider><div className="bg-gray-100 min-h-screen font-sans text-gray-900"><Header activeRoute={route} onNavigate={handleNavigate} /><main>{renderPage()}</main><SiteFormModal /></div></SiteProvider>
    );
}
