# yeojums_ff
quadratic function explorer
import React, { useState } from 'react';

// Types
interface Step1Data {
  positiveShape: string;
  negativeShape: string;
  width: string;
  discovery: string;
}

interface Step2Data {
  vertexFormula: string;
  sameSignPosition: string;
  diffSignPosition: string;
  discovery: string;
}

interface Step3Data {
  yIntercept: string;
  positivePosition: string;
  negativePosition: string;
  cZeroSpecial: string;
  discovery: string;
}

interface ExplorationData {
  step1: Step1Data;
  step2: Step2Data;
  step3: Step3Data;
}

// Constants
const CLASS_LINKS = {
  '1': 'https://b.tkbell.co.kr/tkboard/woi/1243615/070Te5fM12.do?pageSeq=1909631',
  '2': 'https://b.tkbell.co.kr/tkboard/woi/1243615/73eP88436t.do?pageSeq=1909634',
  '3': 'https://b.tkbell.co.kr/tkboard/woi/1243615/0kbNx8eK3a.do?pageSeq=1909636',
  '4': 'https://b.tkbell.co.kr/tkboard/woi/1243615/1z6bIL2c47.do?pageSeq=1909635',
  '5': 'https://b.tkbell.co.kr/tkboard/woi/1243615/G2GsHEERbV.do?pageSeq=1909637',
  '6': 'https://b.tkbell.co.kr/tkboard/woi/1243615/6meBlp16an.do?pageSeq=1909638'
};

// UI Components
const SectionWrapper = ({ title, description, children }) => (
  <section className="bg-white/90 backdrop-blur-sm rounded-2xl p-6 md:p-8 shadow-lg border border-white/20 mb-8 animate-fade-in">
    <h2 className="text-2xl md:text-3xl font-bold text-gray-800 mb-2">{title}</h2>
    <p className="text-gray-600 mb-6">{description}</p>
    {children}
  </section>
);

const QuestionBox = ({ children }) => (
  <div className="bg-blue-50 rounded-xl p-6 mb-6 border border-blue-200">
    <h3 className="text-lg font-bold text-blue-800 mb-4">❓ 탐구 질문</h3>
    <div className="space-y-4">{children}</div>
  </div>
);

const DiscoveryBox = ({ value, onChange, placeholder, name }) => (
  <div className="bg-green-50 rounded-xl p-6 border border-green-200">
    <h3 className="text-lg font-bold text-green-800 mb-4">🔍 나의 발견</h3>
    <textarea
      name={name}
      value={value}
      onChange={onChange}
      placeholder={placeholder}
      rows="4"
      className="w-full p-3 border border-green-300 rounded-lg focus:ring-2 focus:ring-green-500 focus:border-green-500 transition resize-none"
    />
  </div>
);

const FormItem = ({ label, children }) => (
  <div>
    <label className="block text-sm font-semibold text-blue-700 mb-2">{label}</label>
    {children}
  </div>
);

// Step Components
const Step1A = ({ data, onUpdate }) => {
  const handleChange = (e) => {
    onUpdate({ ...data, [e.target.name]: e.target.value });
  };

  return (
    <SectionWrapper
      title="📊 1단계: 계수 a의 변화 탐구"
      description="슬라이더를 이용하여 a의 값을 다양하게 변화시키며 그래프를 관찰하고 아래 질문에 답해보세요."
    >
      <div className="w-full aspect-video mb-8 rounded-lg overflow-hidden border border-gray-200 shadow-md">
        <iframe
          src="https://www.geogebra.org/calculator/f8ttaerd?embed"
          className="w-full h-full"
          allowFullScreen
          style={{ border: 0 }}
          frameBorder="0"
          title="GeoGebra applet for coefficient a"
        ></iframe>
      </div>
      
      <QuestionBox>
        <FormItem label="a > 0일 때 그래프는 어떤 모양인가요?">
          <select name="positiveShape" value={data.positiveShape} onChange={handleChange} className="w-full p-2 border border-gray-300 rounded-md">
            <option value="">선택하세요</option>
            <option value="아래로 볼록">아래로 볼록</option>
            <option value="위로 볼록">위로 볼록</option>
          </select>
        </FormItem>
        <FormItem label="a < 0일 때 그래프는 어떤 모양인가요?">
          <select name="negativeShape" value={data.negativeShape} onChange={handleChange} className="w-full p-2 border border-gray-300 rounded-md">
            <option value="">선택하세요</option>
            <option value="아래로 볼록">아래로 볼록</option>
            <option value="위로 볼록">위로 볼록</option>
          </select>
        </FormItem>
        <FormItem label="|a|의 값이 클수록 그래프의 폭은 어떻게 변하나요?">
          <select name="width" value={data.width} onChange={handleChange} className="w-full p-2 border border-gray-300 rounded-md">
            <option value="">선택하세요</option>
            <option value="넓어진다">넓어진다</option>
            <option value="좁아진다">좁아진다</option>
          </select>
        </FormItem>
      </QuestionBox>
      <DiscoveryBox
        value={data.discovery}
        onChange={handleChange}
        placeholder="계수 a에 대해 발견한 규칙을 자유롭게 써보세요..."
        name="discovery"
      />
    </SectionWrapper>
  );
};

const Step2B = ({ data, onUpdate }) => {
  const handleChange = (e) => {
    onUpdate({ ...data, [e.target.name]: e.target.value });
  };

  return (
    <SectionWrapper
      title="📊 2단계: 계수 b의 변화 탐구"
      description="a = 1로 고정하고, b의 값을 변화시키며 꼭짓점의 위치와 대칭축을 관찰하고 아래 질문에 답해보세요."
    >
      <div className="w-full aspect-video mb-8 rounded-lg overflow-hidden border border-gray-200 shadow-md">
        <iframe
          src="https://www.geogebra.org/calculator/wd5zquyc?embed"
          className="w-full h-full"
          allowFullScreen
          style={{ border: 0 }}
          frameBorder="0"
          title="GeoGebra applet for coefficient b"
        ></iframe>
      </div>

      <QuestionBox>
        <FormItem label="꼭짓점의 x좌표는 어떤 식으로 구할 수 있을까요?">
          <input type="text" name="vertexFormula" value={data.vertexFormula} onChange={handleChange} placeholder="x = ______" className="w-full p-2 border border-gray-300 rounded-md" />
        </FormItem>
        <FormItem label="a와 b의 부호가 같을 때, 대칭축은 y축을 기준으로 어디에 있나요?">
          <select name="sameSignPosition" value={data.sameSignPosition} onChange={handleChange} className="w-full p-2 border border-gray-300 rounded-md">
            <option value="">선택하세요</option>
            <option value="왼쪽">왼쪽</option>
            <option value="오른쪽">오른쪽</option>
          </select>
        </FormItem>
        <FormItem label="a와 b의 부호가 다를 때, 대칭축은 y축을 기준으로 어디에 있나요?">
          <select name="diffSignPosition" value={data.diffSignPosition} onChange={handleChange} className="w-full p-2 border border-gray-300 rounded-md">
            <option value="">선택하세요</option>
            <option value="왼쪽">왼쪽</option>
            <option value="오른쪽">오른쪽</option>
          </select>
        </FormItem>
      </QuestionBox>
      <DiscoveryBox
        value={data.discovery}
        onChange={handleChange}
        placeholder="계수 b에 대해 발견한 규칙을 자유롭게 써보세요..."
        name="discovery"
      />
    </SectionWrapper>
  );
};

const Step3C = ({ data, onUpdate }) => {
  const handleChange = (e) => {
    onUpdate({ ...data, [e.target.name]: e.target.value });
  };

  return (
    <SectionWrapper
      title="📊 3단계: 계수 c의 변화 탐구"
      description="a = 1, b = 0으로 고정하고, c의 값을 변화시키며 y축 교점을 관찰하고 아래 질문에 답해보세요."
    >
      <div className="w-full aspect-video mb-8 rounded-lg overflow-hidden border border-gray-200 shadow-md">
        <iframe
          src="https://www.geogebra.org/calculator/qj7sjb5g?embed"
          className="w-full h-full"
          allowFullScreen
          style={{ border: 0 }}
          frameBorder="0"
          title="GeoGebra applet for coefficient c"
        ></iframe>
      </div>
      
      <QuestionBox>
        <FormItem label="그래프와 y축의 교점의 y좌표는 무엇과 같나요?">
          <input type="text" name="yIntercept" value={data.yIntercept} onChange={handleChange} placeholder="c와 같다? 다르다?" className="w-full p-2 border border-gray-300 rounded-md" />
        </FormItem>
        <FormItem label="c > 0일 때, 그래프는 x축을 기준으로 어디에서 y축과 만나나요?">
          <select name="positivePosition" value={data.positivePosition} onChange={handleChange} className="w-full p-2 border border-gray-300 rounded-md">
            <option value="">선택하세요</option>
            <option value="위쪽">위쪽</option>
            <option value="아래쪽">아래쪽</option>
          </select>
        </FormItem>
        <FormItem label="c < 0일 때, 그래프는 x축을 기준으로 어디에서 y축과 만나나요?">
          <select name="negativePosition" value={data.negativePosition} onChange={handleChange} className="w-full p-2 border border-gray-300 rounded-md">
            <option value="">선택하세요</option>
            <option value="위쪽">위쪽</option>
            <option value="아래쪽">아래쪽</option>
          </select>
        </FormItem>
        <FormItem label="c = 0일 때는 어떤 특별한 점이 있나요?">
          <input type="text" name="cZeroSpecial" value={data.cZeroSpecial} onChange={handleChange} placeholder="특별한 점을 써보세요" className="w-full p-2 border border-gray-300 rounded-md" />
        </FormItem>
      </QuestionBox>
      <DiscoveryBox
        value={data.discovery}
        onChange={handleChange}
        placeholder="계수 c에 대해 발견한 규칙을 자유롭게 써보세요..."
        name="discovery"
      />
    </SectionWrapper>
  );
};

const SummaryCard = ({ title, children }) => (
  <div className="bg-white rounded-xl p-6 shadow-md border border-gray-100 h-full">
    <h4 className="text-xl font-bold text-indigo-700 mb-4">{title}</h4>
    <div className="space-y-3 text-gray-700">{children}</div>
  </div>
);

const SummaryItem = ({ label, value }) => (
  <div>
    <p className="font-semibold text-sm text-gray-500">{label}</p>
    <p className="text-base font-medium">{value || <span className="text-gray-400 italic">입력 없음</span>}</p>
  </div>
);

const DiscoveryItem = ({ value }) => (
  <div className="mt-4 pt-3 border-t">
    <p className="font-semibold text-sm text-teal-600">✨ 내가 발견한 규칙:</p>
    <p className="text-base font-medium whitespace-pre-wrap">{value || <span className="text-gray-400 italic">입력 없음</span>}</p>
  </div>
);

const Confetti = () => {
  const colors = ['#6366f1', '#8b5cf6', '#ec4899', '#10b981', '#f59e0b'];
  return (
    <div className="absolute top-0 left-0 w-full h-full pointer-events-none z-10">
      {Array.from({ length: 50 }).map((_, i) => (
        <div
          key={i}
          className="absolute rounded-full animate-bounce"
          style={{
            backgroundColor: colors[Math.floor(Math.random() * colors.length)],
            left: `${Math.random() * 100}%`,
            width: `${Math.random() * 8 + 4}px`,
            height: `${Math.random() * 8 + 4}px`,
            animationDelay: `${Math.random() * 2}s`,
            animationDuration: '2s',
            top: `${Math.random() * 50}%`
          }}
        />
      ))}
    </div>
  );
};

const Step4Summary = ({ data }) => {
  const [selectedClass, setSelectedClass] = useState('');
  const [showConfetti, setShowConfetti] = useState(false);

  const handleClassSelect = (e) => {
    setSelectedClass(e.target.value);
  };

  const handleSubmit = () => {
    if (selectedClass && CLASS_LINKS[selectedClass]) {
      setShowConfetti(true);
      setTimeout(() => {
        window.open(CLASS_LINKS[selectedClass], '_blank');
        setShowConfetti(false);
      }, 1000);
    } else {
      alert('반을 선택해주세요!');
    }
  };
  
  return (
    <section className="relative bg-white/90 backdrop-blur-sm rounded-2xl p-6 md:p-8 shadow-lg border border-white/20 animate-fade-in overflow-hidden">
      {showConfetti && <Confetti />}
      <h2 className="text-2xl md:text-3xl font-bold text-gray-800 mb-2">🎉 최종 정리: 내가 발견한 이차함수의 비밀!</h2>
      <p className="text-gray-600 mb-6">탐구 활동을 통해 발견한 내용을 확인하고, 자신의 반을 선택하여 결과를 제출해주세요.</p>

      <div className="bg-gray-50 rounded-lg p-6 my-8 border">
        <h3 className="text-xl font-bold text-gray-800 mb-4">📊 나의 탐구 결과 요약</h3>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          <SummaryCard title="계수 a의 역할">
            <SummaryItem label="a > 0일 때 모양" value={data.step1.positiveShape} />
            <SummaryItem label="a < 0일 때 모양" value={data.step1.negativeShape} />
            <SummaryItem label="|a|가 클수록 폭" value={data.step1.width} />
            <DiscoveryItem value={data.step1.discovery} />
          </SummaryCard>
          <SummaryCard title="계수 b의 역할">
            <SummaryItem label="꼭짓점 x좌표" value={data.step2.vertexFormula} />
            <SummaryItem label="a, b 부호 같을 때" value={data.step2.sameSignPosition} />
            <SummaryItem label="a, b 부호 다를 때" value={data.step2.diffSignPosition} />
            <DiscoveryItem value={data.step2.discovery} />
          </SummaryCard>
          <SummaryCard title="계수 c의 역할">
            <SummaryItem label="y축 교점" value={data.step3.yIntercept} />
            <SummaryItem label="c > 0일 때 위치" value={data.step3.positivePosition} />
            <SummaryItem label="c < 0일 때 위치" value={data.step3.negativePosition} />
            <SummaryItem label="c = 0일 때 특징" value={data.step3.cZeroSpecial} />
            <DiscoveryItem value={data.step3.discovery} />
          </SummaryCard>
        </div>
      </div>

      <div className="bg-gradient-to-r from-indigo-50 to-purple-50 rounded-lg p-6 my-6 border border-indigo-200">
        <h3 className="text-xl font-bold text-indigo-800 mb-4">📋 제출하기</h3>
        <p className="mb-4 text-gray-700">자신의 반을 선택하면 해당 반의 팅커벨 보드로 이동합니다.</p>
        <div className="flex flex-col sm:flex-row items-center gap-4">
          <select
            value={selectedClass}
            onChange={handleClassSelect}
            className="w-full sm:w-1/2 p-3 border-2 border-indigo-300 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 transition"
          >
            <option value="">-- 반을 선택하세요 --</option>
            {Object.keys(CLASS_LINKS).map(classNum => (
              <option key={classNum} value={classNum}>{classNum}반</option>
            ))}
          </select>
          <button
            onClick={handleSubmit}
            disabled={!selectedClass}
            className="w-full sm:w-auto py-3 px-8 rounded-lg text-base font-bold cursor-pointer transition transform hover:-translate-y-0.5 bg-gradient-to-r from-green-500 to-teal-600 text-white shadow-md hover:shadow-lg disabled:opacity-50 disabled:cursor-not-allowed disabled:transform-none"
          >
            제출 링크 열기 🚀
          </button>
        </div>
        <p className="mt-4 text-center font-semibold text-indigo-700">
          💡 최종정리를 캡처 후 각반 팅커벨 보드에 올리세요!
        </p>
      </div>

      <div className="mt-8 p-6 bg-yellow-50 rounded-lg border-l-4 border-yellow-400">
        <h4 className="font-bold text-yellow-800">✨ 수고했어요!</h4>
        <p className="text-yellow-700 mt-2">오늘 탐구 활동을 통해 이차함수 그래프의 비밀을 파헤쳤습니다. 이제 여러분은 그래프의 모양을 예측하는 전문가가 되었어요!</p>
      </div>
    </section>
  );
};

// Main Component
const QuadraticFunctionExplorer = () => {
  const [data, setData] = useState({
    step1: {
      positiveShape: '',
      negativeShape: '',
      width: '',
      discovery: ''
    },
    step2: {
      vertexFormula: '',
      sameSignPosition: '',
      diffSignPosition: '',
      discovery: ''
    },
    step3: {
      yIntercept: '',
      positivePosition: '',
      negativePosition: '',
      cZeroSpecial: '',
      discovery: ''
    }
  });

  const updateStep1 = (step1Data) => {
    setData(prev => ({ ...prev, step1: step1Data }));
  };

  const updateStep2 = (step2Data) => {
    setData(prev => ({ ...prev, step2: step2Data }));
  };

  const updateStep3 = (step3Data) => {
    setData(prev => ({ ...prev, step3: step3Data }));
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-100 via-purple-50 to-pink-100">
      {/* Header */}
      <header className="text-center py-12 px-4">
        <h1 className="text-4xl md:text-6xl font-bold bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent mb-4">
          🔬 이차함수 그래프의 비밀 탐구
        </h1>
        <p className="text-lg md:text-xl text-gray-700 max-w-2xl mx-auto">
          y = ax² + bx + c에서 각 계수가 그래프에 어떤 영향을 주는지 알아보는 시간입니다!
        </p>
      </header>

      {/* Main Content */}
      <main className="max-w-6xl mx-auto px-4 pb-12">
        <Step1A data={data.step1} onUpdate={updateStep1} />
        <Step2B data={data.step2} onUpdate={updateStep2} />
        <Step3C data={data.step3} onUpdate={updateStep3} />
        <Step4Summary data={data} />
      </main>

      {/* Custom Styles */}
      <style jsx>{`
        @keyframes fade-in {
          from { opacity: 0; transform: translateY(20px); }
          to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-in {
          animation: fade-in 0.6s ease-out;
        }
      `}</style>
    </div>
  );
};

export default QuadraticFunctionExplorer;
