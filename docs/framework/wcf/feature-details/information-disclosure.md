---
title: Раскрытие информации
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: 0bcf1aa04d7ba7477a6c3f1559a77bbda1f974af
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211958"
---
# <a name="information-disclosure"></a>Раскрытие информации

Раскрытие информации позволяет злоумышленнику получить ценную информацию о системе. Следовательно, всегда обращайте внимание на то, какая информация раскрывается, и может ли ее использовать злоумышленник. Далее перечислены возможные атаки, связанные с раскрытием информации, и способы устранения рисков.

## <a name="message-security-and-http"></a>Безопасность сообщений и HTTP

При использовании безопасности уровня сообщений на транспортном уровне HTTP помните, что безопасность уровня сообщений не обеспечивает защиту заголовков HTTP. Единственный способ защиты заголовков HTTP - использование транспорта HTTPS вместо HTTP. При использовании транспорта HTTPS все сообщение, включая заголовки HTTP, шифруется по протоколу SSL.

## <a name="policy-information"></a>Информация о политике

Обеспечение безопасности политики очень важно, особенно в федеративных сценариях, в которых конфиденциальная информация о требованиях выданного маркера или издателе маркера представлена в политике. В этих случаях рекомендуется обеспечить безопасность конечной точки политики федеративной службы, чтобы помешать злоумышленникам получить информацию о службе, такую как тип утверждений, помещаемых в выданный маркер, или перенаправить клиенты к вредоносным издателям маркеров. Например, злоумышленник может обнаружить пары "имя пользователя/пароль", перенастроив федеративную цепь доверия так, чтобы она завершалась на издателе, выполнившем атаку "злоумышленник в середине". Федеративным клиентам, получающим привязки путем получения политики, рекомендуется убедиться, что они доверяют издателям в полученной федеративной цепи доверия. Дополнительные сведения о сценариях Федерации см. в разделе [Федерация](../../../../docs/framework/wcf/feature-details/federation.md).

## <a name="memory-dumps-can-reveal-claim-information"></a>Дампы памяти, раскрывающие информацию об утверждениях

При сбое приложения в файлах журналов, например, созданных программой Dr. Watson, может содержаться информация об утверждениях. Эту информацию не следует экспортировать в другие сущности, такие как группы поддержки. В противном случае также выполняется экспорт информации об утверждениях, содержащей закрытые данные. Этого можно избежать, если не отправлять файлы журналов неизвестным сущностям.

## <a name="endpoint-addresses"></a>Адреса конечных точек

В адресе конечной точки содержится информация, необходимая для связи с конечной точкой. Безопасность SOAP должна содержать полный адрес в сообщениях согласования безопасности, обмен которыми выполняется для согласования симметричного ключа между клиентом и сервером. Поскольку согласование безопасности является процессом начальной загрузки, заголовки адресов невозможно зашифровать во время этого процесса. Таким образом, в адресах не следует указывать конфиденциальные данные, иначе это приведет к атакам, связанным с раскрытием информации.

## <a name="certificates-transferred-unencrypted"></a>Передача незашифрованных сертификатов

При использовании сертификата X.509 для проверки подлинности клиента сертификат передается в открытом виде, в заголовке SOAP. Помните, что это потенциальное раскрытие личной информации (PII). Это не касается режима `TransportWithMessageCredential`, в котором шифруется все сообщение для обеспечения безопасности на транспортном уровне.

## <a name="service-references"></a>Ссылки на службы

Ссылка на службу - это ссылка на другую службу. Например, служба может передавать клиенту ссылку на службу в ходе выполнения операции. Ссылка на службу также используется с *проверяющим удостоверением доверия*, внутренним компонентом, который гарантирует удостоверение целевого субъекта перед раскрытием информации, такой как данные приложения или учетные данные, в целевом объекте. Если удаленную идентификацию доверия невозможно проверить или она является неверной, отправитель должен убедиться, что никакие данные, способные скомпрометировать его, приложение или пользователя, не были раскрыты.

Ниже представлены способы борьбы с этим.

- Предполагается, что ссылки на службы заслуживают доверия. Будьте внимательны при каждой передаче экземпляров ссылок на службы, убедитесь, что они не подделаны.

- Некоторые приложения могут обеспечивать такое поведение, которое позволяет проводить интерактивное получение доверия, основанное на данных, содержащихся в ссылке на службу, и доверенных данных, проверенных удаленным узлом. WCF предоставляет точки расширения для такого средства, но пользователь должен их реализовать.

## <a name="ntlm"></a>NTLM

По умолчанию в среде домена Windows во время проверки подлинности Windows используется протокол Kerberos для проверки подлинности и авторизации пользователей. Если по какой-либо причине использовать протокол Kerberos невозможно, в качестве резерва используется NT LAN Manager (NTLM). Чтобы отключить такое поведение, необходимо задать для свойства <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> значение `false`. При использовании NTLM необходимо учитывать следующие проблемы.

- NTLM предоставляет имя пользователя клиента. Если необходимо сохранить конфиденциальность имени пользователя, задайте для свойства `AllowNTLM` в привязке значение `false`.

- NTLM не обеспечивает проверки подлинности сервера. Следовательно, клиент не может гарантировать взаимодействие с правильной службой при использовании NTLM в качестве протокола проверки подлинности.

### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Использование NTLM при задании учетных данных клиента или недействительной идентификации

Если при создании клиента указать учетные данные клиента без имени домена или указать недействительную идентификацию сервера, вместо протокола Kerberos будет использоваться NTLM (если для свойства `AllowNtlm` задано значение `true`). Поскольку NTLM не выполняет проверку подлинности сервера, возникает потенциальный риск раскрытия информации.

Например, можно указать учетные данные клиента Windows без доменного имени, как показано в следующем визуальном C# коде.

```csharp
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");
```

В коде не указано имя домена, и, следовательно, будет использоваться NTLM.

Если домен указан, но с помощью функции идентификации конечной точки задано недействительное имя субъекта-службы, то будет использоваться NTLM. Дополнительные сведения о том, как указывается удостоверение конечной точки, см. в разделе [удостоверение службы и проверка подлинности](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).

## <a name="see-also"></a>См. также:

- [Вопросы безопасности](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Повышение привилегий](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Отказ в обслуживании](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Подделка](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Неподдерживаемые сценарии](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [Атаки с повторением](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
