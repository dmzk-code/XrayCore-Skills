# Готовые задания для установленного пакета r3

## Сложная конфигурация
Используй xray-config-orchestrator. Изучи исходный проект, версии клиентского и серверного ядра и реальные ограничения. Подключи только нужные transport/security/protocol references. Собери полные конфигурации сторон и frontend, effective config, peer-map, assumptions, ресурсный бюджет и rollback. Учитывай runtime known issues; отдельно запиши L0, core -test, TCP, UDP, auth, restart и нагрузку. Не трогай рабочие сервисы без разрешения.

## XHTTP split / frontend
Используй orchestrator, xray-transport-xhttp и xray-frontend-topology. Проверь не только network/path, но и extra replacement, выбор HTTP version, реальный session-owner, downloadSettings, XMUX, Host/SNI, buffering/cache/redirects и лимиты headers/body. Два публичных плеча должны попадать в согласованный серверный контекст сессии. Верни client/server/Nginx и проверяемые аварийные сценарии; не объявляй совместимость любого CDN автоматически.

## RAW / REALITY / Vision
Используй orchestrator, xray-transport-raw и xray-protocol-composition. Раздели protocol encryption и transport security, проверь flow по реальной wrapper-ветке. Проверь key formats, shortIds, serverNames, target, TLS1.3 там, где это требуется, и Freedom finalRules. Ключи не публикуй в отчёте. Отдельно проверь первый payload и новый connect после рестарта.

## Миграция старого конфига
Используй xray-legacy-migration и source-audit. Получи effective multi-file config, проверь removed/deprecated/ignored поля, aliases, allowInsecure, mKCP header/seed, proxySettings, reverse, ipsBlocked и finalRules. Сохрани протокол/топологию/теги/credentials, если нет доказанной причины их менять. Дай минимальный diff, совместимую вторую сторону и честный отчёт tests.

## Аудит тяжёлой схемы
Используй orchestrator, dns-routing-balancing, security-sockopt-finalmask и transport skill. Сопоставь HTTP/XMUX/QUIC/Mux окна и connection/session limits, число буферов, rate-параметры, fd/concurrency, mobile keepalive и отказ probes. Не называй все максимальные значения «оптимизацией». Предложи измеряемый профиль с baseline, bounded test и критериями остановки; долгий soak не заменяй коротким echo.

## Обновление знаний на другой релиз
Используй source-audit и update-procedure.md. Не редактируй рабочий checkout. Зафиксируй новый commit, сравни JSON structs/Build/runtime/tests/dependencies и типы транспорта, обнови source provenance, fixtures и regressions. Запусти фактическое ядро новой версии; положительный результат старого pinned бинарника не наследуется.
