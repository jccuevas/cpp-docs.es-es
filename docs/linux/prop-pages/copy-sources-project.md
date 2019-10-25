---
title: Propiedades del proyecto Copiar orígenes (C++ para Linux)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: ceaa1240f08b83ebc83bd7fdc25a3215467eb3f1
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444945"
---
# <a name="copy-sources-project-properties-linux-c"></a>Propiedades del proyecto Copiar orígenes (C++ para Linux)

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

Las propiedades establecidas en esta página de propiedades se aplican a todos los archivos del proyecto, excepto a aquellos cuyas propiedades de nivel de archivo están establecidas.

Propiedad. | DESCRIPCIÓN
--- | ---
Orígenes para copiar | Especifica los orígenes que deben copiarse en el sistema remoto. Si se cambia esta lista, podría modificar o afectar de alguna manera a la estructura de directorios donde se copian los archivos en el sistema remoto.
Copiar orígenes | Especifica si deben copiarse los orígenes en el sistema remoto.
Más orígenes para copiar | Especifica otros orígenes que deben copiarse en el sistema remoto. También se puede proporcionar la lista en forma de pares de asignaciones de local a remoto usando esta sintaxis: rutaDeAccesoLocalCompleta1:=rutaDeAccesoRemotaCompleta1;rutaDeAccesoLocalCompleta2:=rutaDeAccesoRemotaCompleta2, donde un archivo local se puede copiar en la ubicación remota especificada del sistema remoto.

@SourcesToCopyRemotely y @DataFilesToCopyRemotely hacen referencia a los grupos de elementos del archivo de proyecto. Para modificar qué orígenes o archivos de datos se copian de forma remota, edite el archivo *vcxproj* de la siguiente manera:

```xml
<ItemGroup>
   <MyItems Include=“foo.txt” />
   <MyItems Include=“bar.txt” />
   <DataFilesToCopyRemotely Include=”@(MyItems)” />
</ItemGroup>
```

::: moniker-end
