# gql set
1. yarn init
2. new repositary at github.com
3. ./package.json plus to
"scripts": {
  "start": "nodemon --exec ts-node src/index.ts"
},
4. echo "# gql" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/hontips/gql.git
git push -u origin master
5. echo "" > .gitignore, ./.gitignore change to
node_modules
dist
.vscode
6. yarn add -D tslint tslint-config-prettier typescript @types/ws ts-node nodemon
7. npx tslint --init
8. tsc --init, ./tslint.json change to
{
    "defaultSeverity": "error",
    "extends": [
        "tslint:latest",
        "tslint-config-prettier"
    ],
    "jsRules": {},
    "rules": {
        "no-console": false,
        "member-access": false,
        "object-literal-sort-keys": false,
        "ordered-imports": false,
        "interface-name": false
    },
    "rulesDirectory": []
}
9. yarn add graphql-yoga
10. ./tsconfig.json change to
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    "lib": ["dom", "es2017", "esnext.asynciterable"],
    "sourceMap": true,
    "outDir": "./dist",
    "moduleResolution": "node",
 
    "removeComments": true,
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "strictFunctionTypes": true,
    "strictPropertyInitialization": true,
    "noImplicitThis": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": false
  },
  "exclude": ["node_modules"],
  "include": ["./src/**/*.tsx", "./src/**/*.ts"]
}
 
# gql start
1. mkdir src, ./src, create index.ts, ./src/index.ts change to
import { GraphQLServer } from "graphql-yoga";
 
const typeDefs = `
  type Query {
    hello(name: String): String!
  }
`;
 
const resolvers = {
  Query: {
    hello: (_: any, { name }: any) => `hhello ${name || "World"}`
  }
};
 
const server = new GraphQLServer({ typeDefs, resolvers });
server.start(() => console.log("Server is running on localhost:4000"));
2. git push -u origin master

