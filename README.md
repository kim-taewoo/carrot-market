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
```

기존의 복잡한 DB 환경 세팅과 달리 CLI 명령어로 간단히 보안 터널을 통해 PlanetScale과 컴퓨터를 연결할 수 있다. (pscale connect [dbname])
