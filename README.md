import React, { useState, useEffect } from 'react';
import { Camera, Droplets, Activity, Brain, Users, FlaskConical, Thermometer, Heart, Calendar, TrendingUp, AlertCircle, CheckCircle } from 'lucide-react';

const PinnacleEquineMVP = () => {
  const [activeTab, setActiveTab] = useState('dashboard');
  const [selectedHorse, setSelectedHorse] = useState(null);
  const [geneticData, setGeneticData] = useState(null);
  const [supplementPlan, setSupplementPlan] = useState(null);

  // Sample horse data
  const sampleHorses = [
    {
      id: 1,
      name: "Thunder Strike",
      breed: "Thoroughbred",
      age: 5,
      weight: 1100,
      discipline: "Racing",
      geneticProfile: {
        performanceGenes: {
          ACTN3: "RR", // Power gene
          ACE: "II",   // Endurance gene
          MSTN: "CC"   // Muscle development
        },
        healthRisks: ["Joint sensitivity", "Respiratory efficiency"],
        strengths: ["Sprint speed", "Recovery rate"]
      },
      currentSupplements: [
        { name: "Marine Collagen Complex", dosage: "15g daily", effectiveness: 92 },
        { name: "Genetic Performance Blend", dosage: "10g pre-workout", effectiveness: 88 },
        { name: "Recovery Cooling Formula", dosage: "As needed", effectiveness: 95 }
      ],
      performanceMetrics: {
        recentTimes: [1.42, 1.38, 1.35, 1.33, 1.31],
        coatQuality: 94,
        recoveryRate: 87,
        overallHealth: 91
      }
    },
    {
      id: 2,
      name: "Midnight Glory",
      breed: "Arabian",
      age: 7,
      weight: 950,
      discipline: "Endurance",
      geneticProfile: {
        performanceGenes: {
          ACTN3: "RX",
          ACE: "ID",
          MSTN: "TC"
        },
        healthRisks: ["Heat sensitivity"],
        strengths: ["Endurance capacity", "Metabolic efficiency"]
      },
      currentSupplements: [
        { name: "Endurance Microbiome Formula", dosage: "20g daily", effectiveness: 89 },
        { name: "Cooling Therapy Blend", dosage: "Pre-competition", effectiveness: 93 }
      ],
      performanceMetrics: {
        recentTimes: [2.15, 2.12, 2.08, 2.05, 2.03],
        coatQuality: 91,
        recoveryRate: 94,
        overallHealth: 88
      }
    }
  ];

  useEffect(() => {
    if (!selectedHorse && sampleHorses.length > 0) {
      setSelectedHorse(sampleHorses[0]);
      generateSupplementPlan(sampleHorses[0]);
    }
  }, []);

  const generateSupplementPlan = (horse) => {
    // Simulate AI-powered supplement optimization
    const plan = {
      morningDose: {
        marineCollagen: "12g",
        geneticOptimizer: "8g",
        microbiomeSupport: "15g"
      },
      preWorkout: {
        performanceBooster: "10g",
        coolingPrep: "5g"
      },
      postWorkout: {
        recoveryFormula: "20g",
        coolingTherapy: "As needed"
      },
      aiRecommendations: [
        "Increase marine collagen for coat enhancement",
        "Add cooling therapy on hot days (>75°F)",
        "Monitor microbiome response weekly"
      ]
    };
    setSupplementPlan(plan);
  };

  const Dashboard = () => (
    <div className="space-y-6">
      <div className="bg-gradient-to-r from-blue-600 to-purple-600 text-white p-6 rounded-xl">
        <h2 className="text-2xl font-bold mb-2">Welcome to Pinnacle Equine Nutrition</h2>
        <p className="opacity-90">AI-powered personalized nutrition for champion horses</p>
      </div>

      {selectedHorse && (
        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div className="bg-white p-6 rounded-xl shadow-lg border">
            <div className="flex items-center justify-between mb-4">
              <h3 className="text-lg font-semibold">Performance Score</h3>
              <TrendingUp className="text-green-500" />
            </div>
            <div className="text-3xl font-bold text-green-600">
              {selectedHorse.performanceMetrics.overallHealth}%
            </div>
            <p className="text-sm text-gray-600 mt-1">+5% from last month</p>
          </div>

          <div className="bg-white p-6 rounded-xl shadow-lg border">
            <div className="flex items-center justify-between mb-4">
              <h3 className="text-lg font-semibold">Coat Quality</h3>
              <Camera className="text-blue-500" />
            </div>
            <div className="text-3xl font-bold text-blue-600">
              {selectedHorse.performanceMetrics.coatQuality}%
            </div>
            <p className="text-sm text-gray-600 mt-1">Marine collagen working</p>
          </div>

          <div className="bg-white p-6 rounded-xl shadow-lg border">
            <div className="flex items-center justify-between mb-4">
              <h3 className="text-lg font-semibold">Recovery Rate</h3>
              <Activity className="text-purple-500" />
            </div>
            <div className="text-3xl font-bold text-purple-600">
              {selectedHorse.performanceMetrics.recoveryRate}%
            </div>
            <p className="text-sm text-gray-600 mt-1">Optimal cooling therapy</p>
          </div>
        </div>
      )}

      <div className="bg-white p-6 rounded-xl shadow-lg border">
        <h3 className="text-xl font-semibold mb-4">Today's AI Recommendations</h3>
        <div className="space-y-3">
          {supplementPlan?.aiRecommendations.map((rec, index) => (
            <div key={index} className="flex items-start space-x-3 p-3 bg-blue-50 rounded-lg">
              <Brain className="text-blue-600 mt-1 flex-shrink-0" size={16} />
              <p className="text-sm">{rec}</p>
            </div>
          ))}
        </div>
      </div>
    </div>
  );

  const GeneticProfile = () => (
    <div className="space-y-6">
      <div className="bg-white p-6 rounded-xl shadow-lg border">
        <h3 className="text-xl font-semibold mb-4 flex items-center">
          <FlaskConical className="mr-2 text-purple-600" />
          Genetic Analysis Results
        </h3>
        
        {selectedHorse && (
          <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div>
              <h4 className="font-medium mb-3">Performance Genes</h4>
              <div className="space-y-2">
                {Object.entries(selectedHorse.geneticProfile.performanceGenes).map(([gene, variant]) => (
                  <div key={gene} className="flex justify-between items-center p-2 bg-gray-50 rounded">
                    <span className="font-mono text-sm">{gene}</span>
                    <span className="bg-blue-100 text-blue-800 px-2 py-1 rounded text-xs font-medium">
                      {variant}
                    </span>
                  </div>
                ))}
              </div>
            </div>

            <div>
              <h4 className="font-medium mb-3">Genetic Strengths</h4>
              <div className="space-y-2">
                {selectedHorse.geneticProfile.strengths.map((strength, index) => (
                  <div key={index} className="flex items-center space-x-2 p-2 bg-green-50 rounded">
                    <CheckCircle className="text-green-600" size={16} />
                    <span className="text-sm">{strength}</span>
                  </div>
                ))}
              </div>

              <h4 className="font-medium mb-3 mt-4">Health Considerations</h4>
              <div className="space-y-2">
                {selectedHorse.geneticProfile.healthRisks.map((risk, index) => (
                  <div key={index} className="flex items-center space-x-2 p-2 bg-yellow-50 rounded">
                    <AlertCircle className="text-yellow-600" size={16} />
                    <span className="text-sm">{risk}</span>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}
      </div>

      <div className="bg-gradient-to-r from-purple-500 to-pink-500 text-white p-6 rounded-xl">
        <h4 className="text-lg font-semibold mb-2">AI-Optimized Formula Generated</h4>
        <p className="opacity-90">Based on genetic analysis, we've created a personalized supplement blend targeting your horse's specific genetic markers and performance goals.</p>
      </div>
    </div>
  );

  const SmartDosing = () => (
    <div className="space-y-6">
      <div className="bg-white p-6 rounded-xl shadow-lg border">
        <h3 className="text-xl font-semibold mb-4 flex items-center">
          <Droplets className="mr-2 text-blue-600" />
          Today's Smart Dosing Plan
        </h3>

        {supplementPlan && (
          <div className="space-y-4">
            <div className="border-l-4 border-blue-500 pl-4">
              <h4 className="font-medium text-blue-700">Morning Dose (7:00 AM)</h4>
              <div className="mt-2 space-y-1">
                {Object.entries(supplementPlan.morningDose).map(([supplement, dose]) => (
                  <div key={supplement} className="flex justify-between text-sm">
                    <span className="capitalize">{supplement.replace(/([A-Z])/g, ' $1')}</span>
                    <span className="font-medium">{dose}</span>
                  </div>
                ))}
              </div>
            </div>

            <div className="border-l-4 border-green-500 pl-4">
              <h4 className="font-medium text-green-700">Pre-Workout (1 hour before)</h4>
              <div className="mt-2 space-y-1">
                {Object.entries(supplementPlan.preWorkout).map(([supplement, dose]) => (
                  <div key={supplement} className="flex justify-between text-sm">
                    <span className="capitalize">{supplement.replace(/([A-Z])/g, ' $1')}</span>
                    <span className="font-medium">{dose}</span>
                  </div>
                ))}
              </div>
            </div>

            <div className="border-l-4 border-purple-500 pl-4">
              <h4 className="font-medium text-purple-700">Post-Workout Recovery</h4>
              <div className="mt-2 space-y-1">
                {Object.entries(supplementPlan.postWorkout).map(([supplement, dose]) => (
                  <div key={supplement} className="flex justify-between text-sm">
                    <span className="capitalize">{supplement.replace(/([A-Z])/g, ' $1')}</span>
                    <span className="font-medium">{dose}</span>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}
      </div>

      <div className="bg-white p-6 rounded-xl shadow-lg border">
        <h4 className="font-medium mb-3 flex items-center">
          <Thermometer className="mr-2 text-red-500" />
          Environmental Adjustments
        </h4>
        <div className="bg-orange-50 p-4 rounded-lg">
          <p className="text-sm text-orange-800">
            <strong>Weather Alert:</strong> High temperature expected (82°F). 
            Increasing cooling formula dosage by 25% and adding electrolyte boost.
          </p>
        </div>
      </div>
    </div>
  );

  const PlatformFeatures = () => (
    <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
      <div className="bg-gradient-to-br from-blue-500 to-blue-600 text-white p-6 rounded-xl">
        <FlaskConical size={48} className="mb-4" />
        <h3 className="text-xl font-bold mb-2">Genetic Optimizer</h3>
        <p className="opacity-90">AI-powered nutrigenomics processing system analyzing key performance markers like ACTN3, ACE, and MSTN genes.</p>
      </div>

      <div className="bg-gradient-to-br from-green-500 to-green-600 text-white p-6 rounded-xl">
        <Camera size={48} className="mb-4" />
        <h3 className="text-xl font-bold mb-2">Marine Collagen Beauty</h3>
        <p className="opacity-90">Advanced cosmeceutical processing system with computer vision coat analysis and nano-encapsulation technology.</p>
      </div>

      <div className="bg-gradient-to-br from-purple-500 to-purple-600 text-white p-6 rounded-xl">
        <Thermometer size={48} className="mb-4" />
        <h3 className="text-xl font-bold mb-2">Cold Therapy Recovery</h3>
        <p className="opacity-90">Internal cooling optimization system with thermodynamic control and real-time physiological monitoring.</p>
      </div>

      <div className="bg-gradient-to-br from-pink-500 to-pink-600 text-white p-6 rounded-xl">
        <Activity size={48} className="mb-4" />
        <h3 className="text-xl font-bold mb-2">Microbiome Master</h3>
        <p className="opacity-90">Advanced gut microbiome analysis with custom probiotic formulation and metabolic pathway optimization.</p>
      </div>
    </div>
  );

  const tabs = [
    { id: 'dashboard', label: 'Dashboard', icon: TrendingUp },
    { id: 'genetic', label: 'Genetic Profile', icon: FlaskConical },
    { id: 'dosing', label: 'Smart Dosing', icon: Droplets },
    { id: 'features', label: 'Platform Features', icon: Brain }
  ];

  return (
    <div className="min-h-screen bg-gray-50">
      {/* Header */}
      <div className="bg-white shadow-sm border-b">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between items-center h-16">
            <div className="flex items-center space-x-3">
              <div className="bg-gradient-to-r from-blue-600 to-purple-600 p-2 rounded-lg">
                <Heart className="text-white" size={24} />
              </div>
              <div>
                <h1 className="text-xl font-bold text-gray-900">Pinnacle Equine Nutrition</h1>
                <p className="text-xs text-gray-500">AI-Powered Performance Platform</p>
              </div>
            </div>
            
            {selectedHorse && (
              <div className="flex items-center space-x-4">
                <select 
                  className="border rounded-lg px-3 py-2 text-sm"
                  value={selectedHorse.id}
                  onChange={(e) => {
                    const horse = sampleHorses.find(h => h.id === parseInt(e.target.value));
                    setSelectedHorse(horse);
                    generateSupplementPlan(horse);
                  }}
                >
                  {sampleHorses.map(horse => (
                    <option key={horse.id} value={horse.id}>{horse.name}</option>
                  ))}
                </select>
                <div className="text-right">
                  <p className="font-medium text-sm">{selectedHorse.name}</p>
                  <p className="text-xs text-gray-500">{selectedHorse.breed} • {selectedHorse.discipline}</p>
                </div>
              </div>
            )}
          </div>
        </div>
      </div>

      {/* Navigation */}
      <div className="bg-white border-b">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex space-x-8">
            {tabs.map(tab => {
              const Icon = tab.icon;
              return (
                <button
                  key={tab.id}
                  onClick={() => setActiveTab(tab.id)}
                  className={`flex items-center space-x-2 px-3 py-4 border-b-2 text-sm font-medium transition-colors ${
                    activeTab === tab.id
                      ? 'border-blue-500 text-blue-600'
                      : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300'
                  }`}
                >
                  <Icon size={16} />
                  <span>{tab.label}</span>
                </button>
              );
            })}
          </div>
        </div>
      </div>

      {/* Main Content */}
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        {activeTab === 'dashboard' && <Dashboard />}
        {activeTab === 'genetic' && <GeneticProfile />}
        {activeTab === 'dosing' && <SmartDosing />}
        {activeTab === 'features' && <PlatformFeatures />}
      </div>
    </div>
  );
};

export default PinnacleEquineMVP;
