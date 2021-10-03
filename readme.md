#1.
> `git rev-list --format=%B --max-count=1 aefea`
```
commit aefead2207ef7e2aa5dc81a34aedf0cad4c32545
Update CHANGELOG.md
```
#2. 
> `git describe --contains 85024d3`
```
v0.12.23^0
```
#3. 
> `git rev-parse b8d720^@`
```
56cd7859e05c36c06b56d013b55a252d0bb7e158
9ea88f22fc6269854151c571162c5bcf958bee2b
```
#4. 
> `git log --oneline v0.12.24...v0.12.23^`
```
33ff1c03b (tag: v0.12.24) v0.12.24
b14b74c49 [Website] vmc provider links
3f235065b Update CHANGELOG.md
6ae64e247 registry: Fix panic when server is unreachable
5c619ca1b website: Remove links to the getting started guide's old location
06275647e Update CHANGELOG.md
d5f9411f5 command: Fix bug when using terraform login on Windows
4b6d06cc5 Update CHANGELOG.md
dd01a3507 Update CHANGELOG.md
225466bc3 Cleanup after v0.12.23 release
85024d310 (tag: v0.12.23) v0.12.23
```
#5. 
- поиск файла в котором описана функция 

>`grep -r -n 'func providerSource' /d/netology/DevOps/dz_№5/terraform/*` 
```    
/d/netology/DevOps/dz_№5/terraform/provider_source.go:23:func providerSource(configs []*cliconfig.ProviderInstallation, services *disco.Disco) (getproviders.Source, tfdiags.Diagnostics) { 
/d/netology/DevOps/dz_№5/terraform/provider_source.go:187:func providerSourceForCLIConfigLocation(loc cliconfig.ProviderInstallationLocation, services *disco.Disco) (getproviders.Source, tfdiags.Diagnostics) {
```
- вывод первого коммита в котором упоминается функция

>`git log -L :providerSource:provider_source.go --reverse | head | grep commit`
```
commit 8c928e83589d90a031f811fae52a81be7153e82f
```
#6. 
- поиск файла в котором описана функция

>`grep -r -n -i 'func globalPluginDirs' /d/netology/DevOps/dz_№5/terraform/*`
    -/d/netology/DevOps/dz_№5/terraform/plugins.go:18:func globalPluginDirs() []string {

- вывод коммитов в которых упоминается функция

>`git log -L :globalPluginDirs:plugins.go | grep commit`
``` 
    commit 78b12205587fe839f10d946ea3fdc06719decb05
    commit 52dbf94834cb970b510f2fba853a5b49ad9b1a46
    commit 41ab0aef7a0fe030e84018973a64135b11abcd70
    commit 66ebff90cdfaa6938f26f908c7ebad8d547fea17
    commit 8364383c359a6b738a436d1b7745ccdce178df47
```
#7. 
- поиск файла в котором описана функция

>`git log --name-only | grep -i 'synchronized'`
```
synchronized_writers.go
    FullDestroy to the synchronized changes so we can attempt to deduce if
    e2etest server was unsynchronized
    output buffer must be synchronized
    Unsynchronized maps in test
synchronized_writers.go
    The render code path in `template_file` was doing unsynchronized access
```
- поиск автора первог коммита где упомянута функция

>`git log --full-history --reverse -- synchronized_writers.go | head | grep Author`
```
Author: Martin Atkins <mart@degeneration.co.uk>
```
