---
title: Повышенные права доступа для команд dotnet
description: Рекомендации по использованию команд dotnet, которым требуются повышенные права доступа.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 3d874a76eadbf5330c4e5efe4e86bfeca0a9b504
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410632"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="8f7ea-103">Повышенные права доступа для команд dotnet</span><span class="sxs-lookup"><span data-stu-id="8f7ea-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="8f7ea-104">Согласно рекомендациям по разработке программного обеспечения, следует по возможности использовать минимальный уровень прав.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="8f7ea-105">Однако некоторым программам, например средствам мониторинга производительности, согласно правилам операционной системы требуются разрешения администратора.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="8f7ea-106">Ниже описываются поддерживаемые сценарии написания такого ПО с использованием .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span> 

<span data-ttu-id="8f7ea-107">С повышенными правами можно выполнять следующие команды:</span><span class="sxs-lookup"><span data-stu-id="8f7ea-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="8f7ea-108">команды `dotnet tool`, например [dotnet tool install](dotnet-tool-install.md);</span><span class="sxs-lookup"><span data-stu-id="8f7ea-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="8f7ea-109">Выполнять другие команды с повышенными правами не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="8f7ea-110">В частности, мы не рекомендуем выполнять с повышенными правами команды, использующие MSBuild, например [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md) и [dotnet run](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="8f7ea-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="8f7ea-111">Основная проблема связана с управлением разрешениями, когда пользователь переключается между привилегированной учетной записью и учетной записью с ограниченным доступом после выполнения команд dotnet.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="8f7ea-112">У пользователя с ограниченным доступом может не оказаться доступа к файлу, созданному привилегированным пользователем.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="8f7ea-113">Эту проблему можно разрешить, но лучше стараться ее избегать.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="8f7ea-114">Вы можете выполнять команды как привилегированный пользователь, если не будете переключаться между привилегированной учетной записью и учетной записью с ограниченным доступом.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="8f7ea-115">Например, контейнеры Docker по умолчанию выполняются от имени привилегированного пользователя.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="8f7ea-116">Установка глобального средства</span><span class="sxs-lookup"><span data-stu-id="8f7ea-116">Global tool installation</span></span>

<span data-ttu-id="8f7ea-117">Ниже описывается рекомендованный способ установки, запуска и удаления средств .NET Core, для выполнения которых требуется повышенный уровень прав.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="8f7ea-118">Windows</span><span class="sxs-lookup"><span data-stu-id="8f7ea-118">Windows</span></span>](#tab/windows)

### <a name="install-the-global-tool"></a><span data-ttu-id="8f7ea-119">Установка глобального средства</span><span class="sxs-lookup"><span data-stu-id="8f7ea-119">Install the global tool</span></span>

<span data-ttu-id="8f7ea-120">Если папка `%ProgramFiles%\dotnet-tools` уже существует, выполните указанные ниже действия, чтобы проверить, имеет ли группа "Пользователи" разрешение на запись в нее или ее изменение.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

* <span data-ttu-id="8f7ea-121">Щелкните правой кнопкой мыши папку `%ProgramFiles%\dotnet-tools` и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="8f7ea-122">Откроется диалоговое окно **Общие свойства**.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-122">The **Common Properties** dialog box opens.</span></span> 
* <span data-ttu-id="8f7ea-123">Перейдите на вкладку **Безопасность**. В разделе **Группы или пользователи** проверьте, имеет ли группа "Пользователи" разрешение на запись в каталог или его изменение.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span> 
* <span data-ttu-id="8f7ea-124">Если группа "Пользователи" может производить запись в каталог или изменять его, используйте при установке средств другой каталог вместо *dotnet-tools*.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="8f7ea-125">Чтобы установить средства, выполните в командной строке с повышенными привилегиями приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="8f7ea-126">Во время установки будет создана папка *dotnet-tools*.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="8f7ea-127">Запуск глобального средства</span><span class="sxs-lookup"><span data-stu-id="8f7ea-127">Run the global tool</span></span>

<span data-ttu-id="8f7ea-128">**Способ 1**. Используйте полный путь в командной строке с повышенными привилегиями:</span><span class="sxs-lookup"><span data-stu-id="8f7ea-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="8f7ea-129">**Способ 2**. Добавьте созданную папку в `%Path%`.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="8f7ea-130">Это нужно сделать только один раз.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="8f7ea-131">Запустите средство с помощью команды:</span><span class="sxs-lookup"><span data-stu-id="8f7ea-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="8f7ea-132">Удаление глобального средства</span><span class="sxs-lookup"><span data-stu-id="8f7ea-132">Uninstall the global tool</span></span>

<span data-ttu-id="8f7ea-133">В командной строке с повышенными привилегиями введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8f7ea-133">In an elevated prompt, type the following command:</span></span>

```cmd
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[<span data-ttu-id="8f7ea-134">Linux</span><span class="sxs-lookup"><span data-stu-id="8f7ea-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[<span data-ttu-id="8f7ea-135">macOS</span><span class="sxs-lookup"><span data-stu-id="8f7ea-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="8f7ea-136">Локальные средства</span><span class="sxs-lookup"><span data-stu-id="8f7ea-136">Local tools</span></span>

<span data-ttu-id="8f7ea-137">Областью действия локальных средств является дерево подкаталогов отдельного пользователя.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="8f7ea-138">При выполнении с повышенными правами локальные средства предоставляют среде с повышенными правами доступ к среде пользователя с ограниченным доступом.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="8f7ea-139">В Linux и macOS это приводит к тому, что доступ к файлам разрешается только привилегированному пользователю.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="8f7ea-140">Если пользователь перейдет в учетную запись с ограниченным доступом, он утратит доступ к файлам и не сможет производить в них запись.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="8f7ea-141">Поэтому устанавливать средства, требующие повышенных прав, как локальные не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="8f7ea-142">Вместо этого используйте параметр `--tool-path` и приведенные выше инструкции, касающиеся глобальных средств.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="8f7ea-143">Повышение прав во время разработки</span><span class="sxs-lookup"><span data-stu-id="8f7ea-143">Elevation during development</span></span>

<span data-ttu-id="8f7ea-144">Во время разработки вам может требоваться доступ с повышенными правами в целях тестирования приложения.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="8f7ea-145">Например, такое часто бывает в случае с приложениями Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="8f7ea-146">Мы рекомендуем выполнять сборку приложения без повышенных прав, а затем запускать его с повышенными правами.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="8f7ea-147">Есть несколько подходов.</span><span class="sxs-lookup"><span data-stu-id="8f7ea-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="8f7ea-148">Использование созданного исполняемого файла (обеспечивает максимальную производительность при запуске):</span><span class="sxs-lookup"><span data-stu-id="8f7ea-148">Using generated executable (it provides the best startup performance):</span></span>

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- <span data-ttu-id="8f7ea-149">Использование команды [dotnet run](dotnet-run.md) с флагом `—no-build` во избежание создания новых двоичных файлов:</span><span class="sxs-lookup"><span data-stu-id="8f7ea-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="8f7ea-150">См. также</span><span class="sxs-lookup"><span data-stu-id="8f7ea-150">See also</span></span>

* [<span data-ttu-id="8f7ea-151">Обзор глобальных средств .NET Core</span><span class="sxs-lookup"><span data-stu-id="8f7ea-151">.NET Core Global Tools overview</span></span>](global-tools.md)