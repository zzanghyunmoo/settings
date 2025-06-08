settings/
├── inventories/
│   ├── local/
│   │   └── hosts           # 로컬 환경 인벤토리 (localhost)
│   └── example/
│       └── hosts           # 예시 인벤토리(옵션)
├── group_vars/
│   └── all.yml             # 모든 환경에 적용되는 변수
├── roles/
│   └── packages/
│       ├── tasks/
│       │   └── main.yml    # 패키지 설치 작업
│       ├── vars/
│       │   └── main.yml    # 패키지 목록 등 변수
│       ├── handlers/
│       │   └── main.yml    # 필요시 핸들러
│       ├── files/          # 직접 복사할 파일
│       └── templates/      # 템플릿 파일
├── playbooks/
│   ├── mac.yml             # macOS용 플레이북
│   ├── linux.yml           # Linux용 플레이북
│   └── windows.yml         # Windows용 플레이북
├── ansible.cfg             # 앤서블 설정파일
├── requirements.yml        # 필요시 앤서블 갤럭시 역할 정의
└── README.md               # 프로젝트 설명