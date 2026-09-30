# -
성공, 취창업
https://iyuno.wd3.myworkdayjobs.com/careers/job/seoul/ai-agent-engineer_jr101122
https://inthiswork.com/archives/393239
ai-agent-service/
├── .env.example               # 환경 변수 템플릿
├── .gitignore
├── Dockerfile                 # 컨테이너화 설정
├── pyproject.toml             # 의존성 및 프로젝트 메타데이터 (Poetry/Pip)
├── README.md                  # 프로젝트 명세 및 가이드
├── docs/                      # 아키텍처 다이어그램 및 API 문서
│   ├── architecture.md
│   └── sequence_flow.mmd
├── src/                       # 소스코드 루트
│   ├── __init__.py
│   ├── main.py                # FastAPI 애플리케이션 진입점
│   ├── config.py              # 환경 변수 및 설정 관리 (Pydantic Settings)
│   ├── agents/                # 에이전트 오케스트레이션 및 워크플로우
│   │   ├── __init__.py
│   │   ├── base.py            # 베이스 에이전트 및 공통 인터페이스
│   │   ├── workflow.py        # LangGraph 기반 멀티스텝 상태 그래프 정의
│   │   ├── nodes.py           # 에이전트 실행 노드 (생성, 리뷰, 수정 등)
│   │   └── prompts.py         # 페르소나 및 프롬프트 템플릿 관리
│   ├── tools/                 # Tool Calling 및 외부 API 연동
│   │   ├── __init__.py
│   │   ├── registry.py        # 도구 등록 및 스키마 정의 (Function Calling)
│   │   ├── custom_tools.py    # 미디어/번역/검색 등 커스텀 도구 구현
│   │   └── mcp_client.py      # MCP(Model Context Protocol) 클라이언트 연동
│   ├── rag/                   # 검색 증강 생성(RAG) 파이프라인
│   │   ├── __init__.py
│   │   ├── chunker.py         # 문서 정제 및 계층적 청킹 로직
│   │   ├── retriever.py       # 하이브리드 검색기 (Vector + Keyword)
│   │   └── vectorstore.py     # 벡터 DB 연동 (Pinecone, Qdrant 등)
│   ├── core/                  # 공통 인프라 및 핵심 모듈
│   │   ├── __init__.py
│   │   ├── llm.py             # LLM 클라이언트 팩토리 (OpenAI, Anthropic 등)
│   │   ├── telemetry.py       # LLMOps 및 관측 가능성 (LangSmith, Phoenix)
│   │   └── exceptions.py      # 예외 처리 (Tool Failure, Context Loss 대응)
│   └── api/                   # API 엔드포인트 라우터
│       ├── __init__.py
│       ├── schemas.py         # Request/Response Pydantic 모델
│       └── v1/
│           ├── router.py
│           └── endpoints/
│               ├── agent.py   # 에이전트 실행 및 스트리밍 API
│               └── rag.py     # 지식베이스 검색 및 문서 관리 API
├── tests/                     # 테스트 스위트
│   ├── __init__.py
│   ├── unit/                  # 단위 테스트 (도구, 청커 등)
│   ├── integration/           # 통합 테스트 (API 및 LLM 연동)
│   └── evaluation/            # 에이전트 성능 평가 (할루시네이션, 성공률 검증)
└── scripts/                   # 배치 및 운영 스크립트
    ├── ingest_docs.py         # 문서 임베딩 및 인덱싱 배치
    └── evaluate_agent.py      # 에이전트 회귀 테스트 및 평가 스크립트
