# Carrot Market

Serverless Carrot Market Clone using NextJS, Tailwind, Prisma, PlanetScale and Cloudflare.

# STUDY NOTES

## CHAPTER6

```
npm i -D prisma
npx prisma init

brew install planetscale/tap/pscale
brew install mysql-client
brew update pscale

pscale auth login
pscale region list
pscale database create [db name] --region [region name(slug)]
pscale database create carrot-market --region ap-northeast

// *연결
pscale connect carrot-market
// *.env 파일 수정 DATABASE_URL="mysql://127.0.0.1:3306/carrot-market"
// schema 파일 수정 (referentialIntegrity 관련)

// 푸쉬
npx prisma db push

npx prisma studio

// 서버쪽에서 사용
npm i @prisma/client

// node_modules 아래에 타입이 생성됨
npx prisma generate
```

기존의 복잡한 DB 환경 세팅과 달리 CLI 명령어로 간단히 보안 터널을 통해 PlanetScale과 컴퓨터를 연결할 수 있다. (pscale connect [dbname])

### VITESS

스케일을 위한 DB. mysql compatible 이지만 다른 점들이 있다.
foreign key 체크가 엄격하지 않다. 그래서 DB 대신 Prisma 측에서 좀 더 엄격하게 체크하도록 할 수 있다.

foreign key 대상 존재를 보장하기 위해 Prisma 의 도움을 얻는 것.
그걸 위해 `schema.prisma` 파일의 client 설정에 `previewFeature = ["referentialIntegrity"]` 세팅을 하고 db 설정에 `referentialIntegrity = "prisma"` 를 해준다. 베타보다는 좀 더 stable 한 기능인듯

### NEXT.js

API 까지 만들 수 있어서 굳이 node.js 기반의 다른 백엔드 프레임워크를 구축할 필요 없다.
