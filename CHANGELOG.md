# Changelog

All notable changes to this project will be documented in this file. See [standard-version](https://github.com/conventional-changelog/standard-version) for commit guidelines.

### [10.0.3](https://github.com/godaddy/kubernetes-client/compare/10.0.2...10.0.3) (2022-12-22)

### [10.0.2](https://github.com/godaddy/kubernetes-client/compare/10.0.1...10.0.2) (2022-12-22)

### [10.0.1](https://github.com/godaddy/kubernetes-client/compare/10.0.0...10.0.1) (2022-12-22)

## 10.0.0 (2022-12-22)


### ⚠ BREAKING CHANGES

* Kubernetes is at 1.18 and there's little value in maintaining
support for ancient versions.
* **support:** this doesn't include any breaking changes, but our CI integrations
will begin accepting code and using dependencies that are incompatible with Node 6.
* **typings:** this removes support for 1.10.
* **4.X:** This removes the kubernetes-client 4.X API.
* **typings:** This replaces the 4.X declaration file.

Fixes https://github.com/godaddy/kubernetes-client/issues/249
* **README.md:** This commit effectively pivots the Swagger-based client to be
the default, which isn't 100% compatible with the original kubernetes-client
implementation.
* **Node.js support:** EOL for 4 is end of April (https://github.com/nodejs/Release).
We're dropping support a little early in order to leverage some 6+ features for
upcoming improvements (e.g., https://github.com/godaddy/kubernetes-client/pull/207)
* **pods.log:** `pods.log` doesn't follow the kubernetes-client API
conventions. Replace uses of `pods.log('foo')` with `pods('foo').log.get()`.
* **namespaces:** Removes default namespace feature. With a default namespace,
`api.namespaces.get` is potentially ambiguous: get the default namespaces or
get all namespaces. Remove the default namespace to be consistent with other
code.
* **promises:** This removes the (deprecated) `request`-like behavior of
returning a stream when the caller omits a callback. Use `.getStream` (instead
of `.get` without a callback) to get a stream.
* **ReplicationController:** The convenience function for selecting replicationcontroller
pods doesn't follow the kubernetes-client API contract. We're removing it
because it's cumbersome to support with recent changes (*e.g.*, support for
promises and the swagger gen code).

### Features

* ability for a user to specify their own getNames function ([#424](https://github.com/godaddy/kubernetes-client/issues/424)) ([27ec13f](https://github.com/godaddy/kubernetes-client/commit/27ec13f8a44dc380f4458ef34ddbfe507fcb3413)), closes [#418](https://github.com/godaddy/kubernetes-client/issues/418)
* **Add `getStream`:** Addition to resource API ([#119](https://github.com/godaddy/kubernetes-client/issues/119)) ([6268dde](https://github.com/godaddy/kubernetes-client/commit/6268dde8ac877a87837d87e9f5c3282024a0b519))
* **addCustomResourceDefinition:** add support for /status and /scale CRD endpoints ([#335](https://github.com/godaddy/kubernetes-client/issues/335)) ([0511bb4](https://github.com/godaddy/kubernetes-client/commit/0511bb4c0ffa8b2e58416ecdf7bf9978a8706fd2))
* **aliases:** add the nice-to-have aliases to the dynamic client code ([#209](https://github.com/godaddy/kubernetes-client/issues/209)) ([b1b355f](https://github.com/godaddy/kubernetes-client/commit/b1b355f6c2ab2dc95d5b73d608d8ea273a7aa365))
* **auth-provider:** support for auth-provider access-token in fromKubeconfig() ([#112](https://github.com/godaddy/kubernetes-client/issues/112)) ([9b02bc2](https://github.com/godaddy/kubernetes-client/commit/9b02bc276aa8bf310f18f6df58ea16709c7f8399))
* **authentication:** Support OpenID and generic command-based authentication ([#247](https://github.com/godaddy/kubernetes-client/issues/247)) ([98fe599](https://github.com/godaddy/kubernetes-client/commit/98fe5998a0badda559f8323d8458d14099e49d75))
* **auth:** support auth through iam-authenticator, add example ([#332](https://github.com/godaddy/kubernetes-client/issues/332)) ([c06e7cf](https://github.com/godaddy/kubernetes-client/commit/c06e7cfead124ea6f49da856fde150343cf647f9)), closes [#306](https://github.com/godaddy/kubernetes-client/issues/306)
* **backends:** @kubernetes/client-node ([#394](https://github.com/godaddy/kubernetes-client/issues/394)) ([7faef3e](https://github.com/godaddy/kubernetes-client/commit/7faef3edc4c9c7208704a5f84fabd613221ef653))
* **client-node:** add support for watch streaming ([#486](https://github.com/godaddy/kubernetes-client/issues/486)) ([abdaa2a](https://github.com/godaddy/kubernetes-client/commit/abdaa2a45db9d2407fcdb9a5755684d0c73071b6))
* **Client1_10:** add Client class for a specific API version ([#315](https://github.com/godaddy/kubernetes-client/issues/315)) ([3a2886c](https://github.com/godaddy/kubernetes-client/commit/3a2886cf8fed663d7a1778c2d007be6129e6570c))
* **Client:** support passing `undefined` to `Client` ([#474](https://github.com/godaddy/kubernetes-client/issues/474)) ([1fd10c4](https://github.com/godaddy/kubernetes-client/commit/1fd10c4462fda69b0c29f0a3a89ec6095a7f7ce0))
* **config.loadKubeconfig:** helper for loading an API config from ~/.kube/config ([#73](https://github.com/godaddy/kubernetes-client/issues/73)) ([3a9b609](https://github.com/godaddy/kubernetes-client/commit/3a9b609a7a4f24bcfb475d63e6de9724fda0bc18))
* **config:** expose the current namespace on the config object ([#436](https://github.com/godaddy/kubernetes-client/issues/436)) ([d7e0688](https://github.com/godaddy/kubernetes-client/commit/d7e0688f6268c8538077352641c36337b0580205))
* **config:** Now accept a manually specified context in fromKubeConfig ([#82](https://github.com/godaddy/kubernetes-client/issues/82)) ([12738ef](https://github.com/godaddy/kubernetes-client/commit/12738ef433fbbe23244d01866622a63acd6e8fe5))
* **config:** read exec arguments from kubeconfig ([#333](https://github.com/godaddy/kubernetes-client/issues/333)) ([58541c7](https://github.com/godaddy/kubernetes-client/commit/58541c7757083add0c71c19f5c0a22bc2454e7d9))
* **config:** support multiple config files in KUBECONFIG ([#326](https://github.com/godaddy/kubernetes-client/issues/326)) ([d76a84f](https://github.com/godaddy/kubernetes-client/commit/d76a84fa64bdeff28c8f32cd77bc359bf02939b3))
* **core:** add in-cluster config helper ([#49](https://github.com/godaddy/kubernetes-client/issues/49)) ([85915d5](https://github.com/godaddy/kubernetes-client/commit/85915d5595121b21a62d2d66d32a32a3c1b78cb3))
* **CRDs:** add basic CRD support to the dynamic client ([#214](https://github.com/godaddy/kubernetes-client/issues/214)) ([c2aec51](https://github.com/godaddy/kubernetes-client/commit/c2aec51f57fe3a1f25d4d534930b589c3685650a))
* **CRDs:** add Cluster scope support ([#307](https://github.com/godaddy/kubernetes-client/issues/307)) ([cb9f7e4](https://github.com/godaddy/kubernetes-client/commit/cb9f7e43abb48dfa20ae272b3c5863735354e416))
* **CRDs:** cluster-level GET for Namespaced CRDs ([#366](https://github.com/godaddy/kubernetes-client/issues/366)) ([9adcc04](https://github.com/godaddy/kubernetes-client/commit/9adcc04c40dcb1c4ef987fe85000b10e08d47a2a))
* **CustomResourceDefinition:** Add support for CRDs ([#149](https://github.com/godaddy/kubernetes-client/issues/149)) ([4261c2e](https://github.com/godaddy/kubernetes-client/commit/4261c2e63202396667203129829720d1128e4e57))
* **CustomResourceDefinitions:** add support for watch paths ([#233](https://github.com/godaddy/kubernetes-client/issues/233)) ([e09b4ee](https://github.com/godaddy/kubernetes-client/commit/e09b4ee08553105a26862faad342521a0775cbc9))
* **Deployment:** Support for additional Deployment operations ([#103](https://github.com/godaddy/kubernetes-client/issues/103)) ([d802180](https://github.com/godaddy/kubernetes-client/commit/d802180bac6e0fa38b60bf4686d92b460e5ee80e))
* **Deployment:** Support for deployment under apps ([#122](https://github.com/godaddy/kubernetes-client/issues/122)) ([#122](https://github.com/godaddy/kubernetes-client/issues/122)) ([3688d1e](https://github.com/godaddy/kubernetes-client/commit/3688d1eb5e231168254f28a8d082a00e40c94d3a))
* **dynamic clients:** introduce more user-friendly Client classes ([#207](https://github.com/godaddy/kubernetes-client/issues/207)) ([162b33e](https://github.com/godaddy/kubernetes-client/commit/162b33e41456ef6777c157f798dd04f33848c8d5))
* **extensions/thirdpartyresources:** Add `thirdpartyresources` to `Extensions` ([#69](https://github.com/godaddy/kubernetes-client/issues/69)) ([e720491](https://github.com/godaddy/kubernetes-client/commit/e720491a18d275180784bd422bc9051e2532697a))
* **fromKubeconfig:** automatically call `loadKubeconfig` when `kubeconfig` a string ([#251](https://github.com/godaddy/kubernetes-client/issues/251)) ([2898b86](https://github.com/godaddy/kubernetes-client/commit/2898b86f426321a766f1a04ae7b2a84311377c89))
* **getStream:** add support for getStream to swagger-based client code ([#206](https://github.com/godaddy/kubernetes-client/issues/206)) ([ccb2be0](https://github.com/godaddy/kubernetes-client/commit/ccb2be07772efbde9f1414000c779da1ab82a9f3))
* **inCluster:** set serviceaccount root for `inCluster` ([#383](https://github.com/godaddy/kubernetes-client/issues/383)) ([623453d](https://github.com/godaddy/kubernetes-client/commit/623453dffeeaecffc88d1073af061298f67b68ac))
* **insecureSkipTlsVerify:** plumb an option to skip verifying server certs ([#61](https://github.com/godaddy/kubernetes-client/issues/61)) ([901773e](https://github.com/godaddy/kubernetes-client/commit/901773efbdf6b724af4aa9bbe6dccd4aaf84f15c))
* **kube-config:** add support for KUBECONFIG env var ([#322](https://github.com/godaddy/kubernetes-client/issues/322)) ([c6810de](https://github.com/godaddy/kubernetes-client/commit/c6810de22dcfc0ac8a2eadd5df40feddeb03d78c))
* **KubeConfig:** switch to using `KubeConfig` for config handling ([#506](https://github.com/godaddy/kubernetes-client/issues/506)) ([cb94f02](https://github.com/godaddy/kubernetes-client/commit/cb94f02918f36c1c77003d247dbe3cbf0d62f3fa))
* **loadSpec:** change the endpoint called by loadSpec ([#356](https://github.com/godaddy/kubernetes-client/issues/356)) ([8a5f5cb](https://github.com/godaddy/kubernetes-client/commit/8a5f5cb46408f87bdd1b5687efb5b7e52b9df9b5))
* **log:** node-client support for streaming logs ([#488](https://github.com/godaddy/kubernetes-client/issues/488)) ([8be6b5a](https://github.com/godaddy/kubernetes-client/commit/8be6b5aa117be4d4a67899efd340a46f2c35db67))
* **pod-exec:** add initial support for command execution ([#329](https://github.com/godaddy/kubernetes-client/issues/329)) ([ed47d43](https://github.com/godaddy/kubernetes-client/commit/ed47d43bc5c5da44878d710b05b74721843b62fb))
* **Promise API:** Experimental support for a promise-based API ([#133](https://github.com/godaddy/kubernetes-client/issues/133)) ([b5f5e10](https://github.com/godaddy/kubernetes-client/commit/b5f5e10cb5c1a6900043a0482800f99e23e86f62))
* **promises:** if caller doesn't specify a callback, return a promise ([#193](https://github.com/godaddy/kubernetes-client/issues/193)) ([4a84e7f](https://github.com/godaddy/kubernetes-client/commit/4a84e7fcebae15328f8985e20a88ee65ed97f5f5)), closes [#189](https://github.com/godaddy/kubernetes-client/issues/189)
* **request:** add the ability to make the request json option false ([#427](https://github.com/godaddy/kubernetes-client/issues/427)) ([68d8b20](https://github.com/godaddy/kubernetes-client/commit/68d8b20739a5183e6b3cb7c8c8da6ea04cee0093))
* **Send body in DELETE requests:** ([#142](https://github.com/godaddy/kubernetes-client/issues/142)) ([10e4018](https://github.com/godaddy/kubernetes-client/commit/10e40189ce1cfaac6c02629b5ba7354ba8ceb870)), closes [/kubernetes.io/docs/api-reference/v1.7/#delete-58](https://github.com/godaddy//kubernetes.io/docs/api-reference/v1.7//issues/delete-58)
* **Support for more APIs:** Apps, Batch, and RBAC ([#78](https://github.com/godaddy/kubernetes-client/issues/78)) ([3734e12](https://github.com/godaddy/kubernetes-client/commit/3734e12b06be461a42bfe71ef2f0c8df2506021f))
* **swagger:** add files for latest releases ([#415](https://github.com/godaddy/kubernetes-client/issues/415)) ([bfc28bc](https://github.com/godaddy/kubernetes-client/commit/bfc28bc1f97612e7199133ccabf24d6785d28483))
* **Swagger:** experimental support for Swagger. ([#162](https://github.com/godaddy/kubernetes-client/issues/162)) ([f8f1d35](https://github.com/godaddy/kubernetes-client/commit/f8f1d356244055b6bdebe5587c3142d5f69f3ceb))
* **ThirdPartyResource:** Add `resources` option to constructor ([#71](https://github.com/godaddy/kubernetes-client/issues/71)) ([f457b56](https://github.com/godaddy/kubernetes-client/commit/f457b5659677432c21546c1ac1781de080324355))
* **ThirdPartyResources:** add support for Third Party Resources ([#70](https://github.com/godaddy/kubernetes-client/issues/70)) ([58614c5](https://github.com/godaddy/kubernetes-client/commit/58614c5e7117c75a5c7c8401f4d388a8cae5ffeb)), closes [#43](https://github.com/godaddy/kubernetes-client/issues/43)
* **timeout:** plumb a timeout option for HTTP requests ([#339](https://github.com/godaddy/kubernetes-client/issues/339)) ([6a9f06d](https://github.com/godaddy/kubernetes-client/commit/6a9f06d1f77d9ae5b6bcd3341a6c029cf2ac4288))
* **TypeScript:** Initial cut at TypeScript support. ([#174](https://github.com/godaddy/kubernetes-client/issues/174)) ([d3ea455](https://github.com/godaddy/kubernetes-client/commit/d3ea455c9ef242840ff048587e9322e2e6ea7691))
* **typings:** script to generate declaration file for current API ([#313](https://github.com/godaddy/kubernetes-client/issues/313)) ([a8e399c](https://github.com/godaddy/kubernetes-client/commit/a8e399c6652b5c963a8d94d4dfb70219386feb6d))
* **typings:** Update TypeScript declaration file for new API ([#316](https://github.com/godaddy/kubernetes-client/issues/316)) ([fe3a131](https://github.com/godaddy/kubernetes-client/commit/fe3a1313322b5ee6a7421ae8ead718f1537cc126))
* **typings:** upgrade declaration file to 1.13 ([#447](https://github.com/godaddy/kubernetes-client/issues/447)) ([095008e](https://github.com/godaddy/kubernetes-client/commit/095008e8a5c09be49b426dd4b2b33d714a71a845))


### Bug Fixes

* **aliases:** Add missing object aliases ([#54](https://github.com/godaddy/kubernetes-client/issues/54)) ([3cf1e3a](https://github.com/godaddy/kubernetes-client/commit/3cf1e3a65395efa86d8868e7dc95bbefdbcbe0e0))
* **aliases:** reduce the number of nonsense aliases ([#312](https://github.com/godaddy/kubernetes-client/issues/312)) ([f0cd4c7](https://github.com/godaddy/kubernetes-client/commit/f0cd4c7e502cb036cc1f562f6ae77e3cd99d70d9))
* **aliasing:** don't alias apis (to api) ([#393](https://github.com/godaddy/kubernetes-client/issues/393)) ([515a6e3](https://github.com/godaddy/kubernetes-client/commit/515a6e383b7e21c1deafa7cc37539533b21f31e9))
* **auth-provider:** update auth-provider path ([#481](https://github.com/godaddy/kubernetes-client/issues/481)) ([5149309](https://github.com/godaddy/kubernetes-client/commit/5149309615bdbc1076363311791db9cf6777df1e))
* **auth:** remove authentication from /openapi/v2 call ([#372](https://github.com/godaddy/kubernetes-client/issues/372)) ([ef1467a](https://github.com/godaddy/kubernetes-client/commit/ef1467ae9d594d43b975a6fe7f0bcb525c75f45a))
* **auth:** unhandled promise rejection caused by failed auth refresh ([#325](https://github.com/godaddy/kubernetes-client/issues/325)) ([2e3ae71](https://github.com/godaddy/kubernetes-client/commit/2e3ae710326d7790d758fcc9ade25d9830e9a47e))
* **auth:** update auth settings after refreshing ([#338](https://github.com/godaddy/kubernetes-client/issues/338)) ([e8d914b](https://github.com/godaddy/kubernetes-client/commit/e8d914b33a87e2e811c762c275c600fa3a7e6627))
* **backend:** kubernetes-client-node backend support for patch ([#500](https://github.com/godaddy/kubernetes-client/issues/500)) ([43bb7fc](https://github.com/godaddy/kubernetes-client/commit/43bb7fccaed7bbaed351cdc400638f464008a201))
* **client-node:** fixes to @kubernetes/client-node backend ([#498](https://github.com/godaddy/kubernetes-client/issues/498)) ([66e0328](https://github.com/godaddy/kubernetes-client/commit/66e0328af1aa84ca0c2bf5bad7e0d3d7b1b43c39))
* **config:** switched token from base64 to string ([#83](https://github.com/godaddy/kubernetes-client/issues/83)) ([95b75a2](https://github.com/godaddy/kubernetes-client/commit/95b75a20a11674c0ec50620504bf177d24c16796))
* **CRDs:** Fix a filename typo ([#159](https://github.com/godaddy/kubernetes-client/issues/159)) ([6f880fc](https://github.com/godaddy/kubernetes-client/commit/6f880fcfbae9cf4b042082edc8d65e0f195f9a4a))
* **CRDs:** malformed watch paths for namespaced CRDs ([#470](https://github.com/godaddy/kubernetes-client/issues/470)) ([0652b14](https://github.com/godaddy/kubernetes-client/commit/0652b14b038eca04dd58a9ab6f3dc13678a6e03a)), closes [#468](https://github.com/godaddy/kubernetes-client/issues/468)
* **CRDs:** Use `versions` list for spec paths ([#484](https://github.com/godaddy/kubernetes-client/issues/484)) ([3c3111c](https://github.com/godaddy/kubernetes-client/commit/3c3111c0b7f6df29a306d97391d5d7affb549b00)), closes [#458](https://github.com/godaddy/kubernetes-client/issues/458)
* **delete:** `delete` a resource without passing an options object ([#275](https://github.com/godaddy/kubernetes-client/issues/275)) ([36ca19f](https://github.com/godaddy/kubernetes-client/commit/36ca19f817dba8c942834999a60e26230ec9b816))
* **deps:** update dependency camelcase to v6 ([#608](https://github.com/godaddy/kubernetes-client/issues/608)) ([0ed7ef8](https://github.com/godaddy/kubernetes-client/commit/0ed7ef8bc7c597659071ba7f6dd6201489b51ed9))
* **deps:** update dependency swagger-fluent to v5 ([#610](https://github.com/godaddy/kubernetes-client/issues/610)) ([0c0156e](https://github.com/godaddy/kubernetes-client/commit/0c0156e66b22aa4cc39c0e74574d7f28b2a0e999))
* **docs:** typos in docs ([#171](https://github.com/godaddy/kubernetes-client/issues/171)) ([ef65951](https://github.com/godaddy/kubernetes-client/commit/ef659514c406fa4292c7a240e5220b50f2ee6f05))
* **error handling:** handle API errors that aren't JSON ([#60](https://github.com/godaddy/kubernetes-client/issues/60)) ([f8ae84c](https://github.com/godaddy/kubernetes-client/commit/f8ae84c6d04a181594ac396f7472f28df3ea12f4))
* **error handling:** replicate pre-5.0.0 error handling ([#232](https://github.com/godaddy/kubernetes-client/issues/232)) ([b5eb7e0](https://github.com/godaddy/kubernetes-client/commit/b5eb7e0da66b62bef90b186c3041559a2097ae74))
* **examples/:** fix a bug in an example ([#221](https://github.com/godaddy/kubernetes-client/issues/221)) ([dc51f6d](https://github.com/godaddy/kubernetes-client/commit/dc51f6d99d6f375b62aca1c719fd0bd87e1b0ed4))
* **exec:** correctly join URL components ([#402](https://github.com/godaddy/kubernetes-client/issues/402)) ([a557d97](https://github.com/godaddy/kubernetes-client/commit/a557d97b99865c31a96227f0f91e1940a92b77dd))
* **getInCluster:** Use ca.crt correctly ([#87](https://github.com/godaddy/kubernetes-client/issues/87)) ([3c18ebf](https://github.com/godaddy/kubernetes-client/commit/3c18ebfd8b42955eb6b1a99ac49095134852406d))
* **getObjectStream:** for CRDs ([#524](https://github.com/godaddy/kubernetes-client/issues/524)) ([d0b8ecf](https://github.com/godaddy/kubernetes-client/commit/d0b8ecff3b322a7b607203d290d51eba122d0586))
* **greenkeeper:** updating package-lock.json requires npm@5 or later ([#191](https://github.com/godaddy/kubernetes-client/issues/191)) ([ae998bd](https://github.com/godaddy/kubernetes-client/commit/ae998bd7c7d48fd6d2916bcf08ed74576e1efd6b))
* **kubeconfig:** accept relative and absolute paths ([#155](https://github.com/godaddy/kubernetes-client/issues/155)) ([3cbf9cf](https://github.com/godaddy/kubernetes-client/commit/3cbf9cf8cb71b0141e63b4763336d258ce54b04c))
* **kubeconfig:** handle optional kubeconfig user exec properties ([#351](https://github.com/godaddy/kubernetes-client/issues/351)) ([a854fef](https://github.com/godaddy/kubernetes-client/commit/a854fef9166df691d645b46dcdd7a360ceb1d22e))
* **lint:** autofix missing ; ([#235](https://github.com/godaddy/kubernetes-client/issues/235)) ([22dd942](https://github.com/godaddy/kubernetes-client/commit/22dd94263fdf981d19b97e1158d7a602cc29bb7b))
* **loadSpec:** remove noAuth ([#396](https://github.com/godaddy/kubernetes-client/issues/396)) ([4944fba](https://github.com/godaddy/kubernetes-client/commit/4944fba7186e94aae4ba7d589dda67c946be424e))
* **matchLabels:** call BaseObject constructor with correct arguments ([#91](https://github.com/godaddy/kubernetes-client/issues/91)) ([9e1f2d6](https://github.com/godaddy/kubernetes-client/commit/9e1f2d68d0d81afa836920dc35ecf223c8445a14)), closes [#90](https://github.com/godaddy/kubernetes-client/issues/90) [/github.com/godaddy/kubernetes-client/commit/d083f93be23182f4a629c02cdd319692a09168f8#diff-86b75ecfbd25aa771c8e9e0dff8eb00fL25](https://github.com/godaddy//github.com/godaddy/kubernetes-client/commit/d083f93be23182f4a629c02cdd319692a09168f8/issues/diff-86b75ecfbd25aa771c8e9e0dff8eb00fL25)
* **namespaces:** api.namespaces('foo') usage ([#190](https://github.com/godaddy/kubernetes-client/issues/190)) ([816b957](https://github.com/godaddy/kubernetes-client/commit/816b9571b2468db2bba1c613321a3f10a8b0c2d8)), closes [#187](https://github.com/godaddy/kubernetes-client/issues/187) [#169](https://github.com/godaddy/kubernetes-client/issues/169)
* **node6:** remove spread for node6+ support ([#368](https://github.com/godaddy/kubernetes-client/issues/368)) ([2e161aa](https://github.com/godaddy/kubernetes-client/commit/2e161aa74e5f60334961011103a43515c7d465b2))
* **package:** update @kubernetes/client-node to version 0.10.0 ([#495](https://github.com/godaddy/kubernetes-client/issues/495)) ([eb83d4a](https://github.com/godaddy/kubernetes-client/commit/eb83d4acd4b7ce44b45e12272ecd6ac2472f1b14))
* **package:** update @kubernetes/client-node to version 0.10.2 ([#503](https://github.com/godaddy/kubernetes-client/issues/503)) ([76dc3a7](https://github.com/godaddy/kubernetes-client/commit/76dc3a773230aa7dcac023c6c44048b67b74f80c))
* **package:** update @kubernetes/client-node to version 0.9.0 ([#487](https://github.com/godaddy/kubernetes-client/issues/487)) ([238fbb6](https://github.com/godaddy/kubernetes-client/commit/238fbb66ba10e8e3b65b6ecf9c9567fbe3c4e624))
* **package:** update deepmerge to version 4.0.0 ([#514](https://github.com/godaddy/kubernetes-client/issues/514)) ([400475a](https://github.com/godaddy/kubernetes-client/commit/400475a4e0120771b133aa2579fabb24371d1bfb))
* **package:** update fluent-openapi to version 0.1.1 ([#311](https://github.com/godaddy/kubernetes-client/issues/311)) ([50ac41f](https://github.com/godaddy/kubernetes-client/commit/50ac41f921f3a1ef2ae92afc94ef53a9e15336e4))
* **package:** update openid-client to version 2.0.0 ([#252](https://github.com/godaddy/kubernetes-client/issues/252)) ([877af3d](https://github.com/godaddy/kubernetes-client/commit/877af3d77d95ba9b4458109e19aa32e751b0ec81))
* **package:** update openid-client to version 3.0.0 ([#459](https://github.com/godaddy/kubernetes-client/issues/459)) ([66d5b73](https://github.com/godaddy/kubernetes-client/commit/66d5b73c9523ff251e19b319f3321a259a241287))
* **package:** update openid-client to version 3.1.0 ([#463](https://github.com/godaddy/kubernetes-client/issues/463)) ([2211ed2](https://github.com/godaddy/kubernetes-client/commit/2211ed2d38640f30cd1a139e15741e4262c30464))
* **package:** update ws to version 7.0.0 ([#453](https://github.com/godaddy/kubernetes-client/issues/453)) ([1d507c4](https://github.com/godaddy/kubernetes-client/commit/1d507c459e1e5f28faf059347988aa5d0068fd0f))
* **pod-exec:** fix for 403 throws ([#543](https://github.com/godaddy/kubernetes-client/issues/543)) ([88c43d8](https://github.com/godaddy/kubernetes-client/commit/88c43d8023be9fd51be583940d8fa0e9412e21de))
* **querystring:**  indices must be disabled ([#344](https://github.com/godaddy/kubernetes-client/issues/344)) ([c6bb0a1](https://github.com/godaddy/kubernetes-client/commit/c6bb0a1393444ad920d510f4f9a6b729d78399f8))
* **README:** modified group example to be correct ([#94](https://github.com/godaddy/kubernetes-client/issues/94)) ([73e4f05](https://github.com/godaddy/kubernetes-client/commit/73e4f055e298296e41466766164621e3b1114c01))
* **request:** handle 200 responses with an empty body ([#381](https://github.com/godaddy/kubernetes-client/issues/381)) ([5672a3c](https://github.com/godaddy/kubernetes-client/commit/5672a3c73ba98ac518ceec4569a916f64b668531))
* **require:** update auth-provider path ([#397](https://github.com/godaddy/kubernetes-client/issues/397)) ([67d114a](https://github.com/godaddy/kubernetes-client/commit/67d114afc3ea883f79064d8e3bd7dfc58eb7d0c3))
* **response `content-type` checking:** more robust JSON response handling ([#89](https://github.com/godaddy/kubernetes-client/issues/89)) ([ace816e](https://github.com/godaddy/kubernetes-client/commit/ace816e21c5ab84ca885073d0f3e3fe16a7735ca))
* **swagger:** Fallback to old swagger.json endpoint ([#364](https://github.com/godaddy/kubernetes-client/issues/364)) ([42f3e5d](https://github.com/godaddy/kubernetes-client/commit/42f3e5dfdc08cd040a00d66de0bc01915c73411d))
* **typings:** address issue with typings support for promises ([#253](https://github.com/godaddy/kubernetes-client/issues/253)) ([4fc1eb0](https://github.com/godaddy/kubernetes-client/commit/4fc1eb0ef99ee813222acf555739543310c18a72))
* **typings:** Include typings with npm package. ([#179](https://github.com/godaddy/kubernetes-client/issues/179)) ([42f4735](https://github.com/godaddy/kubernetes-client/commit/42f47353837e98a9b22b6f1d644505e33ca1fd19))
* **typings:** remove `.loadSpec()` from declarations ([#406](https://github.com/godaddy/kubernetes-client/issues/406)) ([b17a0a9](https://github.com/godaddy/kubernetes-client/commit/b17a0a9cd0df455c7507fd567a69f8ad5da50a1c))
* **undefined `options` passed to `.get`:** set default `options` value to `{}` ([#115](https://github.com/godaddy/kubernetes-client/issues/115)) ([b2df448](https://github.com/godaddy/kubernetes-client/commit/b2df4484682d7c8070ad40452a804354c0e903c7)), closes [/github.com/godaddy/kubernetes-client/issues/37#issuecomment-259434515](https://github.com/godaddy//github.com/godaddy/kubernetes-client/issues/37/issues/issuecomment-259434515)
* **Update broken unit test:** remove incorrect usage of nock.matchHeader ([#114](https://github.com/godaddy/kubernetes-client/issues/114)) ([5469623](https://github.com/godaddy/kubernetes-client/commit/5469623c77ce47b862c7513f527f243d815b935b))


* **4.X:** remove old API code ([#317](https://github.com/godaddy/kubernetes-client/issues/317)) ([6a3aa8b](https://github.com/godaddy/kubernetes-client/commit/6a3aa8b7efce536e4c8cb6277e693ce3db889740))
* **Node.js support:** Drop support for Node.js 4 and 5 ([#208](https://github.com/godaddy/kubernetes-client/issues/208)) ([e70f9cb](https://github.com/godaddy/kubernetes-client/commit/e70f9cba58df472a48aaa659e255e3bc82319412))
* **pods.log:** remove the deprarecated `pods.log` function. ([#196](https://github.com/godaddy/kubernetes-client/issues/196)) ([29a7935](https://github.com/godaddy/kubernetes-client/commit/29a79358c4965a0766f4c4fd3668a963359226b7))
* **README.md:** Re-write README.md for the Swagger-based client ([#222](https://github.com/godaddy/kubernetes-client/issues/222)) ([42d5bc7](https://github.com/godaddy/kubernetes-client/commit/42d5bc774d87e9688fa7c0c042eeeb0e8a994166))
* remove support for 1.7, 1.8, and 1.9 ([#622](https://github.com/godaddy/kubernetes-client/issues/622)) ([de189a6](https://github.com/godaddy/kubernetes-client/commit/de189a65fcf7cc5c3d711c7508e8beacbea4d444))
* **ReplicationController:** remove replicationcontrollers.pods feature ([#192](https://github.com/godaddy/kubernetes-client/issues/192)) ([d728814](https://github.com/godaddy/kubernetes-client/commit/d7288142ad3cfbd3e02645300a8ff286e8dc8c14))
* **support:** drop support for Node 6 ([#465](https://github.com/godaddy/kubernetes-client/issues/465)) ([523800d](https://github.com/godaddy/kubernetes-client/commit/523800d32cd18576adb1f5938af50db903bb6c62))

## [9.0.0](https://github.com/godaddy/kubernetes-client/compare/8.3.7...9.0.0) (2020-05-01)


### ⚠ BREAKING CHANGES

* Kubernetes is at 1.18 and there's little value in maintaining
support for ancient versions.

* remove support for 1.7, 1.8, and 1.9 ([#622](https://github.com/godaddy/kubernetes-client/issues/622)) ([de189a6](https://github.com/godaddy/kubernetes-client/commit/de189a65fcf7cc5c3d711c7508e8beacbea4d444))

### [8.3.7](https://github.com/godaddy/kubernetes-client/compare/8.3.6...8.3.7) (2020-04-09)


### Bug Fixes

* **deps:** update dependency camelcase to v6 ([#608](https://github.com/godaddy/kubernetes-client/issues/608)) ([0ed7ef8](https://github.com/godaddy/kubernetes-client/commit/0ed7ef8bc7c597659071ba7f6dd6201489b51ed9))
* **deps:** update dependency swagger-fluent to v5 ([#610](https://github.com/godaddy/kubernetes-client/issues/610)) ([0c0156e](https://github.com/godaddy/kubernetes-client/commit/0c0156e66b22aa4cc39c0e74574d7f28b2a0e999))

### [8.3.6](https://github.com/godaddy/kubernetes-client/compare/8.3.5...8.3.6) (2019-11-21)

### [8.3.5](https://github.com/godaddy/kubernetes-client/compare/8.3.4...8.3.5) (2019-11-03)


### Bug Fixes

* **pod-exec:** fix for 403 throws ([#543](https://github.com/godaddy/kubernetes-client/issues/543)) ([88c43d8](https://github.com/godaddy/kubernetes-client/commit/88c43d8))

### [8.3.4](https://github.com/godaddy/kubernetes-client/compare/8.3.3...8.3.4) (2019-08-22)

### [8.3.3](https://github.com/godaddy/kubernetes-client/compare/8.3.2...8.3.3) (2019-07-23)


### Bug Fixes

* **getObjectStream:** for CRDs ([#524](https://github.com/godaddy/kubernetes-client/issues/524)) ([d0b8ecf](https://github.com/godaddy/kubernetes-client/commit/d0b8ecf))



### [8.3.2](https://github.com/godaddy/kubernetes-client/compare/8.3.1...8.3.2) (2019-07-23)


### Bug Fixes

* **package:** update deepmerge to version 4.0.0 ([#514](https://github.com/godaddy/kubernetes-client/issues/514)) ([400475a](https://github.com/godaddy/kubernetes-client/commit/400475a))



### [8.3.1](https://github.com/godaddy/kubernetes-client/compare/8.3.0...8.3.1) (2019-07-02)



## [8.3.0](https://github.com/godaddy/kubernetes-client/compare/8.2.1...8.3.0) (2019-06-25)


### Features

* **KubeConfig:** switch to using `KubeConfig` for config handling ([#506](https://github.com/godaddy/kubernetes-client/issues/506)) ([cb94f02](https://github.com/godaddy/kubernetes-client/commit/cb94f02))



### [8.2.1](https://github.com/godaddy/kubernetes-client/compare/8.2.0...8.2.1) (2019-06-22)


### Bug Fixes

* **backend:** kubernetes-client-node backend support for patch ([#500](https://github.com/godaddy/kubernetes-client/issues/500)) ([43bb7fc](https://github.com/godaddy/kubernetes-client/commit/43bb7fc))
* **client-node:** fixes to @kubernetes/client-node backend ([#498](https://github.com/godaddy/kubernetes-client/issues/498)) ([66e0328](https://github.com/godaddy/kubernetes-client/commit/66e0328))
* **package:** update @kubernetes/client-node to version 0.10.0 ([#495](https://github.com/godaddy/kubernetes-client/issues/495)) ([eb83d4a](https://github.com/godaddy/kubernetes-client/commit/eb83d4a))
* **package:** update @kubernetes/client-node to version 0.10.2 ([#503](https://github.com/godaddy/kubernetes-client/issues/503)) ([76dc3a7](https://github.com/godaddy/kubernetes-client/commit/76dc3a7))


### Tests

* **patch:** add integration test for `.patch` ([#492](https://github.com/godaddy/kubernetes-client/issues/492)) ([92d9729](https://github.com/godaddy/kubernetes-client/commit/92d9729))



## [8.2.0](https://github.com/godaddy/kubernetes-client/compare/8.1.3...8.2.0) (2019-05-31)


### Bug Fixes

* **package:** update @kubernetes/client-node to version 0.9.0 ([#487](https://github.com/godaddy/kubernetes-client/issues/487)) ([238fbb6](https://github.com/godaddy/kubernetes-client/commit/238fbb6))


### Features

* **client-node:** add support for watch streaming ([#486](https://github.com/godaddy/kubernetes-client/issues/486)) ([abdaa2a](https://github.com/godaddy/kubernetes-client/commit/abdaa2a))
* **log:** node-client support for streaming logs ([#488](https://github.com/godaddy/kubernetes-client/issues/488)) ([8be6b5a](https://github.com/godaddy/kubernetes-client/commit/8be6b5a))



### [8.1.3](https://github.com/godaddy/kubernetes-client/compare/8.1.2...8.1.3) (2019-05-29)


### Bug Fixes

* **CRDs:** Use `versions` list for spec paths ([#484](https://github.com/godaddy/kubernetes-client/issues/484)) ([3c3111c](https://github.com/godaddy/kubernetes-client/commit/3c3111c)), closes [#458](https://github.com/godaddy/kubernetes-client/issues/458)



### [8.1.2](https://github.com/godaddy/kubernetes-client/compare/8.1.1...8.1.2) (2019-05-23)


### Bug Fixes

* **auth-provider:** update auth-provider path ([#481](https://github.com/godaddy/kubernetes-client/issues/481)) ([5149309](https://github.com/godaddy/kubernetes-client/commit/5149309))


### Tests

* **integration:** add more integration tests ([#480](https://github.com/godaddy/kubernetes-client/issues/480)) ([1d3948a](https://github.com/godaddy/kubernetes-client/commit/1d3948a))
* **integration:** add start of integration testing framework ([#477](https://github.com/godaddy/kubernetes-client/issues/477)) ([d9543a1](https://github.com/godaddy/kubernetes-client/commit/d9543a1))



### [8.1.1](https://github.com/godaddy/kubernetes-client/compare/8.1.0...8.1.1) (2019-05-20)



## [8.1.0](https://github.com/godaddy/kubernetes-client/compare/8.0.0...8.1.0) (2019-05-19)


### Features

* **backends:** @kubernetes/client-node ([#394](https://github.com/godaddy/kubernetes-client/issues/394)) ([7faef3e](https://github.com/godaddy/kubernetes-client/commit/7faef3e))
* **Client:** support passing `undefined` to `Client` ([#474](https://github.com/godaddy/kubernetes-client/issues/474)) ([1fd10c4](https://github.com/godaddy/kubernetes-client/commit/1fd10c4))


### Tests

* **update:** use  new config handling API ([#475](https://github.com/godaddy/kubernetes-client/issues/475)) ([669352b](https://github.com/godaddy/kubernetes-client/commit/669352b))



## [8.0.0](https://github.com/godaddy/kubernetes-client/compare/7.0.1...8.0.0) (2019-05-19)


### Bug Fixes

* **CRDs:** malformed watch paths for namespaced CRDs ([#470](https://github.com/godaddy/kubernetes-client/issues/470)) ([0652b14](https://github.com/godaddy/kubernetes-client/commit/0652b14)), closes [#468](https://github.com/godaddy/kubernetes-client/issues/468)
* **package:** update openid-client to version 3.0.0 ([#459](https://github.com/godaddy/kubernetes-client/issues/459)) ([66d5b73](https://github.com/godaddy/kubernetes-client/commit/66d5b73))
* **package:** update openid-client to version 3.1.0 ([#463](https://github.com/godaddy/kubernetes-client/issues/463)) ([2211ed2](https://github.com/godaddy/kubernetes-client/commit/2211ed2))
* **package:** update ws to version 7.0.0 ([#453](https://github.com/godaddy/kubernetes-client/issues/453)) ([1d507c4](https://github.com/godaddy/kubernetes-client/commit/1d507c4))


### chore

* **support:** drop support for Node 6 ([#465](https://github.com/godaddy/kubernetes-client/issues/465)) ([523800d](https://github.com/godaddy/kubernetes-client/commit/523800d))


### BREAKING CHANGES

* **support:** this doesn't include any breaking changes, but our CI integrations
will begin accepting code and using dependencies that are incompatible with Node 6.



## [7.0.1](https://github.com/godaddy/kubernetes-client/compare/7.0.0...7.0.1) (2019-05-07)



# [7.0.0](https://github.com/godaddy/kubernetes-client/compare/6.12.1...7.0.0) (2019-04-23)


### Features

* **typings:** upgrade declaration file to 1.13 ([#447](https://github.com/godaddy/kubernetes-client/issues/447)) ([095008e](https://github.com/godaddy/kubernetes-client/commit/095008e))


### BREAKING CHANGES

* **typings:** this removes support for 1.10.



## [6.12.1](https://github.com/godaddy/kubernetes-client/compare/6.12.0...6.12.1) (2019-04-02)



# [6.12.0](https://github.com/godaddy/kubernetes-client/compare/6.11.1...6.12.0) (2019-04-01)


### Features

* **config:** expose the current namespace on the config object ([#436](https://github.com/godaddy/kubernetes-client/issues/436)) ([d7e0688](https://github.com/godaddy/kubernetes-client/commit/d7e0688))



<a name="6.10.0"></a>
# [6.10.0](https://github.com/godaddy/kubernetes-client/compare/6.8.3...6.10.0) (2019-03-04)


### Features

* **swagger:** add files for latest releases ([#415](https://github.com/godaddy/kubernetes-client/issues/415)) ([bfc28bc](https://github.com/godaddy/kubernetes-client/commit/bfc28bc))
* ability for a user to specify their own getNames function ([#424](https://github.com/godaddy/kubernetes-client/issues/424)) ([27ec13f](https://github.com/godaddy/kubernetes-client/commit/27ec13f)), closes [#418](https://github.com/godaddy/kubernetes-client/issues/418)



<a name="6.9.0"></a>
# [6.9.0](https://github.com/godaddy/kubernetes-client/compare/6.8.3...6.9.0) (2019-02-21)


### Features

* **swagger:** add files for latest releases ([#415](https://github.com/godaddy/kubernetes-client/issues/415)) ([bfc28bc](https://github.com/godaddy/kubernetes-client/commit/bfc28bc))



<a name="6.8.3"></a>
## [6.8.3](https://github.com/godaddy/kubernetes-client/compare/6.8.2...6.8.3) (2019-01-28)


### Bug Fixes

* **exec:** correctly join URL components ([#402](https://github.com/godaddy/kubernetes-client/issues/402)) ([a557d97](https://github.com/godaddy/kubernetes-client/commit/a557d97))



<a name="6.8.2"></a>
## [6.8.2](https://github.com/godaddy/kubernetes-client/compare/6.8.1...6.8.2) (2019-01-28)


### Bug Fixes

* **typings:** remove `.loadSpec()` from declarations ([#406](https://github.com/godaddy/kubernetes-client/issues/406)) ([b17a0a9](https://github.com/godaddy/kubernetes-client/commit/b17a0a9))



<a name="6.8.1"></a>
## [6.8.1](https://github.com/godaddy/kubernetes-client/compare/6.7.1...6.8.1) (2019-01-12)


### Bug Fixes

* **loadSpec:** remove noAuth ([#396](https://github.com/godaddy/kubernetes-client/issues/396)) ([4944fba](https://github.com/godaddy/kubernetes-client/commit/4944fba))
* **require:** update auth-provider path ([#397](https://github.com/godaddy/kubernetes-client/issues/397)) ([67d114a](https://github.com/godaddy/kubernetes-client/commit/67d114a))



<a name="6.8.0"></a>
# [6.8.0](https://github.com/godaddy/kubernetes-client/compare/6.5.1...6.8.0) (2019-01-11)


### Bug Fixes

* **aliasing:** don't alias apis (to api) ([#393](https://github.com/godaddy/kubernetes-client/issues/393)) ([515a6e3](https://github.com/godaddy/kubernetes-client/commit/515a6e3))
* **auth:** remove authentication from /openapi/v2 call ([#372](https://github.com/godaddy/kubernetes-client/issues/372)) ([ef1467a](https://github.com/godaddy/kubernetes-client/commit/ef1467a))
* **request:** handle 200 responses with an empty body ([#381](https://github.com/godaddy/kubernetes-client/issues/381)) ([5672a3c](https://github.com/godaddy/kubernetes-client/commit/5672a3c))
* **require:** update auth-provider path ([#397](https://github.com/godaddy/kubernetes-client/issues/397)) ([67d114a](https://github.com/godaddy/kubernetes-client/commit/67d114a))


### Features

* **inCluster:** set serviceaccount root for `inCluster` ([#383](https://github.com/godaddy/kubernetes-client/issues/383)) ([623453d](https://github.com/godaddy/kubernetes-client/commit/623453d))



<a name="6.7.1"></a>
## [6.7.1](https://github.com/godaddy/kubernetes-client/compare/6.7.0...6.7.1) (2019-01-04)


### Bug Fixes

* **aliasing:** don't alias apis (to api) ([#393](https://github.com/godaddy/kubernetes-client/issues/393)) ([515a6e3](https://github.com/godaddy/kubernetes-client/commit/515a6e3))



<a name="6.7.0"></a>
# [6.7.0](https://github.com/godaddy/kubernetes-client/compare/6.6.2...6.7.0) (2018-12-29)


### Features

* **inCluster:** set serviceaccount root for `inCluster` ([#383](https://github.com/godaddy/kubernetes-client/issues/383)) ([623453d](https://github.com/godaddy/kubernetes-client/commit/623453d))



<a name="6.6.2"></a>
## [6.6.2](https://github.com/godaddy/kubernetes-client/compare/6.6.1...6.6.2) (2018-12-29)



<a name="6.6.1"></a>
## [6.6.1](https://github.com/godaddy/kubernetes-client/compare/6.6.0...6.6.1) (2018-12-24)


### Bug Fixes

* **request:** handle 200 responses with an empty body ([#381](https://github.com/godaddy/kubernetes-client/issues/381)) ([5672a3c](https://github.com/godaddy/kubernetes-client/commit/5672a3c))



<a name="6.6.0"></a>
# [6.6.0](https://github.com/godaddy/kubernetes-client/compare/6.3.2...6.6.0) (2018-12-24)


### Bug Fixes

* **auth:** remove authentication from /openapi/v2 call ([#372](https://github.com/godaddy/kubernetes-client/issues/372)) ([ef1467a](https://github.com/godaddy/kubernetes-client/commit/ef1467a))
* **node6:** remove spread for node6+ support ([#368](https://github.com/godaddy/kubernetes-client/issues/368)) ([2e161aa](https://github.com/godaddy/kubernetes-client/commit/2e161aa))
* **swagger:** Fallback to old swagger.json endpoint ([#364](https://github.com/godaddy/kubernetes-client/issues/364)) ([42f3e5d](https://github.com/godaddy/kubernetes-client/commit/42f3e5d))


### Features

* **CRDs:** cluster-level GET for Namespaced CRDs ([#366](https://github.com/godaddy/kubernetes-client/issues/366)) ([9adcc04](https://github.com/godaddy/kubernetes-client/commit/9adcc04))
* **loadSpec:** change the endpoint called by loadSpec ([#356](https://github.com/godaddy/kubernetes-client/issues/356)) ([8a5f5cb](https://github.com/godaddy/kubernetes-client/commit/8a5f5cb))



<a name="6.5.1"></a>
## [6.5.1](https://github.com/godaddy/kubernetes-client/compare/6.5.0...6.5.1) (2018-12-11)


### Bug Fixes

* **node6:** remove spread for node6+ support ([#368](https://github.com/godaddy/kubernetes-client/issues/368)) ([2e161aa](https://github.com/godaddy/kubernetes-client/commit/2e161aa))



<a name="6.5.0"></a>
# [6.5.0](https://github.com/godaddy/kubernetes-client/compare/6.4.1...6.5.0) (2018-12-05)


### Features

* **CRDs:** cluster-level GET for Namespaced CRDs ([#366](https://github.com/godaddy/kubernetes-client/issues/366)) ([9adcc04](https://github.com/godaddy/kubernetes-client/commit/9adcc04))



<a name="6.4.1"></a>
## [6.4.1](https://github.com/godaddy/kubernetes-client/compare/6.4.0...6.4.1) (2018-11-27)


### Bug Fixes

* **swagger:** Fallback to old swagger.json endpoint ([#364](https://github.com/godaddy/kubernetes-client/issues/364)) ([42f3e5d](https://github.com/godaddy/kubernetes-client/commit/42f3e5d))



<a name="6.4.0"></a>
# [6.4.0](https://github.com/godaddy/kubernetes-client/compare/6.3.0...6.4.0) (2018-11-12)


### Bug Fixes

* **kubeconfig:** handle optional kubeconfig user exec properties ([#351](https://github.com/godaddy/kubernetes-client/issues/351)) ([a854fef](https://github.com/godaddy/kubernetes-client/commit/a854fef))
* **querystring:**  indices must be disabled ([#344](https://github.com/godaddy/kubernetes-client/issues/344)) ([c6bb0a1](https://github.com/godaddy/kubernetes-client/commit/c6bb0a1))


### Features

* **loadSpec:** change the endpoint called by loadSpec ([#356](https://github.com/godaddy/kubernetes-client/issues/356)) ([8a5f5cb](https://github.com/godaddy/kubernetes-client/commit/8a5f5cb))



<a name="6.3.2"></a>
## [6.3.2](https://github.com/godaddy/kubernetes-client/compare/6.3.1...6.3.2) (2018-10-31)



<a name="6.3.1"></a>
## [6.3.1](https://github.com/godaddy/kubernetes-client/compare/6.3.0...6.3.1) (2018-10-31)


### Bug Fixes

* **kubeconfig:** handle optional kubeconfig user exec properties ([#351](https://github.com/godaddy/kubernetes-client/issues/351)) ([a854fef](https://github.com/godaddy/kubernetes-client/commit/a854fef))
* **querystring:**  indices must be disabled ([#344](https://github.com/godaddy/kubernetes-client/issues/344)) ([c6bb0a1](https://github.com/godaddy/kubernetes-client/commit/c6bb0a1))



<a name="6.3.0"></a>
# [6.3.0](https://github.com/godaddy/kubernetes-client/compare/6.2.0...6.3.0) (2018-10-19)


### Bug Fixes

* **auth:** update auth settings after refreshing ([#338](https://github.com/godaddy/kubernetes-client/issues/338)) ([e8d914b](https://github.com/godaddy/kubernetes-client/commit/e8d914b))


### Features

* **timeout:** plumb a timeout option for HTTP requests ([#339](https://github.com/godaddy/kubernetes-client/issues/339)) ([6a9f06d](https://github.com/godaddy/kubernetes-client/commit/6a9f06d))



<a name="6.2.0"></a>
# [6.2.0](https://github.com/godaddy/kubernetes-client/compare/6.1.0...6.2.0) (2018-10-19)


### Features

* **addCustomResourceDefinition:** add support for /status and /scale CRD endpoints ([#335](https://github.com/godaddy/kubernetes-client/issues/335)) ([0511bb4](https://github.com/godaddy/kubernetes-client/commit/0511bb4))
* **auth:** support auth through iam-authenticator, add example ([#332](https://github.com/godaddy/kubernetes-client/issues/332)) ([c06e7cf](https://github.com/godaddy/kubernetes-client/commit/c06e7cf)), closes [#306](https://github.com/godaddy/kubernetes-client/issues/306)
* **config:** read exec arguments from kubeconfig ([#333](https://github.com/godaddy/kubernetes-client/issues/333)) ([58541c7](https://github.com/godaddy/kubernetes-client/commit/58541c7))
* **config:** support multiple config files in KUBECONFIG ([#326](https://github.com/godaddy/kubernetes-client/issues/326)) ([d76a84f](https://github.com/godaddy/kubernetes-client/commit/d76a84f))
* **pod-exec:** add initial support for command execution ([#329](https://github.com/godaddy/kubernetes-client/issues/329)) ([ed47d43](https://github.com/godaddy/kubernetes-client/commit/ed47d43))



<a name="6.1.0"></a>
# [6.1.0](https://github.com/godaddy/kubernetes-client/compare/6.0.1...6.1.0) (2018-09-06)


### Bug Fixes

* **auth:** unhandled promise rejection caused by failed auth refresh ([#325](https://github.com/godaddy/kubernetes-client/issues/325)) ([2e3ae71](https://github.com/godaddy/kubernetes-client/commit/2e3ae71))


### Features

* **kube-config:** add support for KUBECONFIG env var ([#322](https://github.com/godaddy/kubernetes-client/issues/322)) ([c6810de](https://github.com/godaddy/kubernetes-client/commit/c6810de))



<a name="6.0.1"></a>
## [6.0.1](https://github.com/godaddy/kubernetes-client/compare/6.0.0...6.0.1) (2018-09-04)



<a name="6.0.0"></a>
# [6.0.0](https://github.com/godaddy/kubernetes-client/compare/5.4.0...6.0.0) (2018-08-28)


### Bug Fixes

* **aliases:** reduce the number of nonsense aliases ([#312](https://github.com/godaddy/kubernetes-client/issues/312)) ([f0cd4c7](https://github.com/godaddy/kubernetes-client/commit/f0cd4c7))
* **package:** update fluent-openapi to version 0.1.1 ([#311](https://github.com/godaddy/kubernetes-client/issues/311)) ([50ac41f](https://github.com/godaddy/kubernetes-client/commit/50ac41f))


### Chores

* **4.X:** remove old API code ([#317](https://github.com/godaddy/kubernetes-client/issues/317)) ([6a3aa8b](https://github.com/godaddy/kubernetes-client/commit/6a3aa8b))


### Features

* **Client1_10:** add Client class for a specific API version ([#315](https://github.com/godaddy/kubernetes-client/issues/315)) ([3a2886c](https://github.com/godaddy/kubernetes-client/commit/3a2886c))
* **typings:** script to generate declaration file for current API ([#313](https://github.com/godaddy/kubernetes-client/issues/313)) ([a8e399c](https://github.com/godaddy/kubernetes-client/commit/a8e399c))
* **typings:** Update TypeScript declaration file for new API ([#316](https://github.com/godaddy/kubernetes-client/issues/316)) ([fe3a131](https://github.com/godaddy/kubernetes-client/commit/fe3a131))


### BREAKING CHANGES

* **4.X:** This removes the kubernetes-client 4.X API.
* **typings:** This replaces the 4.X declaration file.

Fixes https://github.com/godaddy/kubernetes-client/issues/249



<a name="5.4.0"></a>
# [5.4.0](https://github.com/godaddy/kubernetes-client/compare/5.3.1...5.4.0) (2018-08-07)


### Features

* **CRDs:** add Cluster scope support ([#307](https://github.com/godaddy/kubernetes-client/issues/307)) ([cb9f7e4](https://github.com/godaddy/kubernetes-client/commit/cb9f7e4))



<a name="5.3.1"></a>
## [5.3.1](https://github.com/godaddy/kubernetes-client/compare/5.3.0...5.3.1) (2018-06-27)


### Bug Fixes

* **delete:** `delete` a resource without passing an options object ([#275](https://github.com/godaddy/kubernetes-client/issues/275)) ([36ca19f](https://github.com/godaddy/kubernetes-client/commit/36ca19f))



<a name="5.3.0"></a>
# [5.3.0](https://github.com/godaddy/kubernetes-client/compare/5.2.0...5.3.0) (2018-05-16)


### Bug Fixes

* **package:** update openid-client to version 2.0.0 ([#252](https://github.com/godaddy/kubernetes-client/issues/252)) ([877af3d](https://github.com/godaddy/kubernetes-client/commit/877af3d))
* **typings:** address issue with typings support for promises ([#253](https://github.com/godaddy/kubernetes-client/issues/253)) ([4fc1eb0](https://github.com/godaddy/kubernetes-client/commit/4fc1eb0))


### Features

* **fromKubeconfig:** automatically call `loadKubeconfig` when `kubeconfig` a string ([#251](https://github.com/godaddy/kubernetes-client/issues/251)) ([2898b86](https://github.com/godaddy/kubernetes-client/commit/2898b86))



<a name="5.2.0"></a>
# [5.2.0](https://github.com/godaddy/kubernetes-client/compare/5.1.0...5.2.0) (2018-04-05)


### Features

* **authentication:** Support OpenID and generic command-based authentication ([#247](https://github.com/godaddy/kubernetes-client/issues/247)) ([98fe599](https://github.com/godaddy/kubernetes-client/commit/98fe599))



<a name="5.1.0"></a>
# [5.1.0](https://github.com/godaddy/kubernetes-client/compare/5.0.1...5.1.0) (2018-03-16)


### Bug Fixes

* **lint:** autofix missing ; ([#235](https://github.com/godaddy/kubernetes-client/issues/235)) ([22dd942](https://github.com/godaddy/kubernetes-client/commit/22dd942))


### Features

* **CustomResourceDefinitions:** add support for watch paths ([#233](https://github.com/godaddy/kubernetes-client/issues/233)) ([e09b4ee](https://github.com/godaddy/kubernetes-client/commit/e09b4ee))



<a name="5.0.1"></a>
## [5.0.1](https://github.com/godaddy/kubernetes-client/compare/5.0.0...5.0.1) (2018-03-15)


### Bug Fixes

* **error handling:** replicate pre-5.0.0 error handling ([#232](https://github.com/godaddy/kubernetes-client/issues/232)) ([b5eb7e0](https://github.com/godaddy/kubernetes-client/commit/b5eb7e0))



<a name="5.0.0"></a>
# [5.0.0](https://github.com/godaddy/kubernetes-client/compare/4.0.1...5.0.0) (2018-03-15)


### Bug Fixes

* **examples/:** fix a bug in an example ([#221](https://github.com/godaddy/kubernetes-client/issues/221)) ([dc51f6d](https://github.com/godaddy/kubernetes-client/commit/dc51f6d))


### Chores

* **Node.js support:** Drop support for Node.js 4 and 5 ([#208](https://github.com/godaddy/kubernetes-client/issues/208)) ([e70f9cb](https://github.com/godaddy/kubernetes-client/commit/e70f9cb))


### Documentation

* **README.md:** Re-write README.md for the Swagger-based client ([#222](https://github.com/godaddy/kubernetes-client/issues/222)) ([42d5bc7](https://github.com/godaddy/kubernetes-client/commit/42d5bc7))


### Features

* **aliases:** add the nice-to-have aliases to the dynamic client code ([#209](https://github.com/godaddy/kubernetes-client/issues/209)) ([b1b355f](https://github.com/godaddy/kubernetes-client/commit/b1b355f))
* **CRDs:** add basic CRD support to the dynamic client ([#214](https://github.com/godaddy/kubernetes-client/issues/214)) ([c2aec51](https://github.com/godaddy/kubernetes-client/commit/c2aec51))
* **dynamic clients:** introduce more user-friendly Client classes ([#207](https://github.com/godaddy/kubernetes-client/issues/207)) ([162b33e](https://github.com/godaddy/kubernetes-client/commit/162b33e))
* **getStream:** add support for getStream to swagger-based client code ([#206](https://github.com/godaddy/kubernetes-client/issues/206)) ([ccb2be0](https://github.com/godaddy/kubernetes-client/commit/ccb2be0))


### BREAKING CHANGES

* **README.md:** This commit effectively pivots the Swagger-based client to be
the default, which isn't 100% compatible with the original kubernetes-client
implementation.
* **Node.js support:** EOL for 4 is end of April (https://github.com/nodejs/Release).
We're dropping support a little early in order to leverage some 6+ features for
upcoming improvements (e.g., https://github.com/godaddy/kubernetes-client/pull/207)



<a name="4.0.1"></a>
## [4.0.1](https://github.com/godaddy/kubernetes-client/compare/4.0.0...4.0.1) (2018-03-07)



<a name="4.0.0"></a>
# [4.0.0](https://github.com/godaddy/kubernetes-client/compare/3.18.1...4.0.0) (2018-02-13)


### Bug Fixes

* **greenkeeper:** updating package-lock.json requires npm@5 or later ([#191](https://github.com/godaddy/kubernetes-client/issues/191)) ([ae998bd](https://github.com/godaddy/kubernetes-client/commit/ae998bd))
* **namespaces:** api.namespaces('foo') usage ([#190](https://github.com/godaddy/kubernetes-client/issues/190)) ([816b957](https://github.com/godaddy/kubernetes-client/commit/816b957)), closes [#187](https://github.com/godaddy/kubernetes-client/issues/187) [#169](https://github.com/godaddy/kubernetes-client/issues/169)


### Chores

* **pods.log:** remove the deprarecated `pods.log` function. ([#196](https://github.com/godaddy/kubernetes-client/issues/196)) ([29a7935](https://github.com/godaddy/kubernetes-client/commit/29a7935))
* **ReplicationController:** remove replicationcontrollers.pods feature ([#192](https://github.com/godaddy/kubernetes-client/issues/192)) ([d728814](https://github.com/godaddy/kubernetes-client/commit/d728814))


### Features

* **promises:** if caller doesn't specify a callback, return a promise ([#193](https://github.com/godaddy/kubernetes-client/issues/193)) ([4a84e7f](https://github.com/godaddy/kubernetes-client/commit/4a84e7f)), closes [#189](https://github.com/godaddy/kubernetes-client/issues/189)
* **Swagger:** experimental support for Swagger. ([#162](https://github.com/godaddy/kubernetes-client/issues/162)) ([f8f1d35](https://github.com/godaddy/kubernetes-client/commit/f8f1d35))


### BREAKING CHANGES

* **pods.log:** `pods.log` doesn't follow the kubernetes-client API
conventions. Replace uses of `pods.log('foo')` with `pods('foo').log.get()`.
* **namespaces:** Removes default namespace feature. With a default namespace,
`api.namespaces.get` is potentially ambiguous: get the default namespaces or
get all namespaces. Remove the default namespace to be consistent with other
code.
* **promises:** This removes the (deprecated) `request`-like behavior of
returning a stream when the caller omits a callback. Use `.getStream` (instead
of `.get` without a callback) to get a stream.
* **ReplicationController:** The convenience function for selecting replicationcontroller
pods doesn't follow the kubernetes-client API contract. We're removing it
because it's cumbersome to support with recent changes (*e.g.*, support for
promises and the swagger gen code).



<a name="3.18.1"></a>
## [3.18.1](https://github.com/godaddy/kubernetes-client/compare/3.18.0...3.18.1) (2018-01-26)


### Bug Fixes

* **typings:** Include typings with npm package. ([#179](https://github.com/godaddy/kubernetes-client/issues/179)) ([42f4735](https://github.com/godaddy/kubernetes-client/commit/42f4735))



<a name="3.18.0"></a>
# [3.18.0](https://github.com/godaddy/kubernetes-client/compare/3.17.2...3.18.0) (2018-01-18)


### Bug Fixes

* **docs:** typos in docs ([#171](https://github.com/godaddy/kubernetes-client/issues/171)) ([ef65951](https://github.com/godaddy/kubernetes-client/commit/ef65951))


### Features

* **TypeScript:** Initial cut at TypeScript support. ([#174](https://github.com/godaddy/kubernetes-client/issues/174)) ([d3ea455](https://github.com/godaddy/kubernetes-client/commit/d3ea455))



<a name="3.17.2"></a>
## [3.17.2](https://github.com/godaddy/kubernetes-client/compare/3.17.1...3.17.2) (2018-01-05)



<a name="3.17.1"></a>
## [3.17.1](https://github.com/godaddy/kubernetes-client/compare/3.17.0...v3.17.1) (2017-11-14)


### Bug Fixes

* **CRDs:** Fix a filename typo (#159) ([6f880fc](https://github.com/godaddy/kubernetes-client/commit/6f880fc)), closes [#159](https://github.com/godaddy/kubernetes-client/issues/159)



<a name="3.17.0"></a>
# [3.17.0](https://github.com/godaddy/kubernetes-client/compare/3.16.1...v3.17.0) (2017-11-14)


### Features

* **CustomResourceDefinition:** Add support for CRDs (#149) ([4261c2e](https://github.com/godaddy/kubernetes-client/commit/4261c2e))



<a name="3.16.1"></a>
## [3.16.1](https://github.com/godaddy/kubernetes-client/compare/3.16.0...v3.16.1) (2017-11-08)


### Bug Fixes

* **kubeconfig:** accept relative and absolute paths (#155) ([3cbf9cf](https://github.com/godaddy/kubernetes-client/commit/3cbf9cf))



<a name="3.16.0"></a>
# [3.16.0](https://github.com/godaddy/kubernetes-client/compare/3.14.0...v3.16.0) (2017-09-28)


### Features

* **Promise API:** Experimental support for a promise-based API (#133) ([b5f5e10](https://github.com/godaddy/kubernetes-client/commit/b5f5e10))
* **Send body in DELETE requests:** (#142) ([10e4018](https://github.com/godaddy/kubernetes-client/commit/10e4018))



<a name="3.15.0"></a>
# [3.15.0](https://github.com/godaddy/kubernetes-client/compare/3.14.0...v3.15.0) (2017-08-29)


### Features

* **Send body in DELETE requests:** (#142) ([10e4018](https://github.com/godaddy/kubernetes-client/commit/10e4018))



<a name="3.14.0"></a>
# [3.14.0](https://github.com/godaddy/kubernetes-client/compare/3.12.0...v3.14.0) (2017-08-01)


### Bug Fixes

* **undefined `options` passed to `.get`:** set default `options` value to `{}` (#115) ([b2df448](https://github.com/godaddy/kubernetes-client/commit/b2df448))
* **Update broken unit test:** remove incorrect usage of nock.matchHeader (#114) ([5469623](https://github.com/godaddy/kubernetes-client/commit/5469623))


### Features

* **Add `getStream`:** Addition to resource API (#119) ([6268dde](https://github.com/godaddy/kubernetes-client/commit/6268dde))
* **Deployment:** Support for deployment under apps (#122) (#122) ([3688d1e](https://github.com/godaddy/kubernetes-client/commit/3688d1e))



<a name="3.13.0"></a>
# [3.13.0](https://github.com/godaddy/kubernetes-client/compare/3.12.0...3.13.0) (2017-07-29)


### Bug Fixes

* **undefined `options` passed to `.get`:** set default `options` value to `{}` ([#115](https://github.com/godaddy/kubernetes-client/issues/115)) ([b2df448](https://github.com/godaddy/kubernetes-client/commit/b2df448))
* **Update broken unit test:** remove incorrect usage of nock.matchHeader ([#114](https://github.com/godaddy/kubernetes-client/issues/114)) ([5469623](https://github.com/godaddy/kubernetes-client/commit/5469623))


### Features

* **Add `getStream`:** Addition to resource API ([#119](https://github.com/godaddy/kubernetes-client/issues/119)) ([6268dde](https://github.com/godaddy/kubernetes-client/commit/6268dde))



<a name="3.12.0"></a>
# [3.12.0](https://github.com/godaddy/kubernetes-client/compare/3.11.0...v3.12.0) (2017-06-15)


### Features

* **auth-provider:** support for auth-provider access-token in fromKubeconfig() (#112) ([9b02bc2](https://github.com/godaddy/kubernetes-client/commit/9b02bc2))



<a name="3.11.0"></a>
# [3.11.0](https://github.com/godaddy/kubernetes-client/compare/3.10.1...v3.11.0) (2017-05-31)


### Bug Fixes

* **README:** modified group example to be correct (#94) ([73e4f05](https://github.com/godaddy/kubernetes-client/commit/73e4f05))


### Features

* **Deployment:** Support for additional Deployment operations (#103) ([d802180](https://github.com/godaddy/kubernetes-client/commit/d802180))



<a name="3.10.1"></a>
## [3.10.1](https://github.com/godaddy/kubernetes-client/compare/3.10.0...v3.10.1) (2017-03-09)


### Bug Fixes

* **matchLabels:** call BaseObject constructor with correct arguments (#91) ([9e1f2d6](https://github.com/godaddy/kubernetes-client/commit/9e1f2d6))



<a name="3.10.0"></a>
# [3.10.0](https://github.com/godaddy/kubernetes-client/compare/3.8.0...v3.10.0) (2017-03-03)


### Bug Fixes

* **response `content-type` checking:** more robust JSON response handling (#89) ([ace816e](https://github.com/godaddy/kubernetes-client/commit/ace816e))


### Features

* **Support for more APIs:** Apps, Batch, and RBAC (#78) ([3734e12](https://github.com/godaddy/kubernetes-client/commit/3734e12))



<a name="3.9.0"></a>
# [3.9.0](https://github.com/godaddy/kubernetes-client/compare/3.8.0...v3.9.0) (2017-02-27)


### Features

* **Support for more APIs:** Apps, Batch, and RBAC (#78) ([3734e12](https://github.com/godaddy/kubernetes-client/commit/3734e12))



<a name="3.8.0"></a>
# [3.8.0](https://github.com/godaddy/kubernetes-client/compare/3.5.1...v3.8.0) (2017-02-25)


### Bug Fixes

* **config:** switched token from base64 to string (#83) ([95b75a2](https://github.com/godaddy/kubernetes-client/commit/95b75a2))
* **getInCluster:** Use ca.crt correctly (#87) ([3c18ebf](https://github.com/godaddy/kubernetes-client/commit/3c18ebf))


### Features

* **config:** Now accept a manually specified context in fromKubeConfig (#82) ([12738ef](https://github.com/godaddy/kubernetes-client/commit/12738ef))



<a name="3.7.0"></a>
# [3.7.0](https://github.com/godaddy/kubernetes-client/compare/3.4.0...v3.7.0) (2017-02-25)


### Bug Fixes

* **config:** switched token from base64 to string (#83) ([95b75a2](https://github.com/godaddy/kubernetes-client/commit/95b75a2))


### Features

* **config:** Now accept a manually specified context in fromKubeConfig (#82) ([12738ef](https://github.com/godaddy/kubernetes-client/commit/12738ef))



<a name="3.6.0"></a>
# [3.6.0](https://github.com/godaddy/kubernetes-client/compare/3.5.1...v3.6.0) (2017-02-24)


### Features

* **config:** Now accept a manually specified context in fromKubeConfig (#82) ([12738ef](https://github.com/godaddy/kubernetes-client/commit/12738ef))



<a name="3.5.1"></a>
## [3.5.1](https://github.com/godaddy/kubernetes-client/compare/3.5.0...v3.5.1) (2017-02-23)



<a name="3.5.0"></a>
# [3.5.0](https://github.com/godaddy/kubernetes-client/compare/3.3.0...v3.5.0) (2017-02-14)


### Features

* **config.loadKubeconfig:** helper for loading an API config from ~/.kube/config (#73) ([3a9b609](https://github.com/godaddy/kubernetes-client/commit/3a9b609))



<a name="3.4.0"></a>
# [3.4.0](https://github.com/godaddy/kubernetes-client/compare/3.3.0...v3.4.0) (2017-02-13)


### Features

* **config.loadKubeconfig:** helper for loading an API config from ~/.kube/config (#73) ([3a9b609](https://github.com/godaddy/kubernetes-client/commit/3a9b609))



<a name="3.3.0"></a>
# [3.3.0](https://github.com/godaddy/kubernetes-client/compare/3.1.0...v3.3.0) (2017-02-09)


### Bug Fixes

* **error handling:** handle API errors that aren't JSON (#60) ([f8ae84c](https://github.com/godaddy/kubernetes-client/commit/f8ae84c))


### Features

* **extensions/thirdpartyresources:** Add `thirdpartyresources` to `Extensions` (#69) ([e720491](https://github.com/godaddy/kubernetes-client/commit/e720491))
* **insecureSkipTlsVerify:** plumb an option to skip verifying server certs (#61) ([901773e](https://github.com/godaddy/kubernetes-client/commit/901773e))
* **ThirdPartyResource:** Add `resources` option to constructor (#71) ([f457b56](https://github.com/godaddy/kubernetes-client/commit/f457b56))
* **ThirdPartyResources:** add support for Third Party Resources (#70) ([58614c5](https://github.com/godaddy/kubernetes-client/commit/58614c5)), closes [#43](https://github.com/godaddy/kubernetes-client/issues/43)



<a name="3.2.0"></a>
# [3.2.0](https://github.com/godaddy/kubernetes-client/compare/3.1.0...v3.2.0) (2017-01-20)


### Bug Fixes

* **error handling:** handle API errors that aren't JSON (#60) ([f8ae84c](https://github.com/godaddy/kubernetes-client/commit/f8ae84c))


### Features

* **insecureSkipTlsVerify:** plumb an option to skip verifying server certs (#61) ([901773e](https://github.com/godaddy/kubernetes-client/commit/901773e))



<a name="3.1.0"></a>
# [3.1.0](https://github.com/godaddy/kubernetes-client/compare/3.0.0...3.1.0) (2016-12-24)


### Bug Fixes

* **aliases:** Add missing object aliases (#54) ([3cf1e3a](https://github.com/godaddy/kubernetes-client/commit/3cf1e3a))


### Features

* **core:** add in-cluster config helper (#49) ([85915d5](https://github.com/godaddy/kubernetes-client/commit/85915d5))
