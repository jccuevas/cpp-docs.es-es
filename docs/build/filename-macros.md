---
title: Macros de nombre de archivo
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
ms.openlocfilehash: 2e7552d77d753d4e93734f2fc9a35b3b68d8d55c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457699"
---
# <a name="filename-macros"></a>Macros de nombre de archivo

Macros de nombre de archivo están predefinidas como nombres de archivo especificados en la dependencia (especificaciones de nombre de archivo no completa en disco). Estas macros no es necesario ir entre paréntesis cuando invoca; Especifique solo un $ tal como se muestra.

|Macro|Significado|
|-----------|-------------|
|**$\@**|Nombre del destino actual completa (ruta de acceso, nombre base, extensión), como se especifica actualmente.|
|**$$\@**|Nombre del destino actual completa (ruta de acceso, nombre base, extensión), como se especifica actualmente. Válido solo como una dependencia en una dependencia.|
|**$&#42;**|Del destino actual ruta de acceso y nombre base sin extensión de archivo.|
|**$&#42;&#42;**|Todos los dependientes del destino actual.|
|**$?**|Todos los dependientes con una marca de tiempo posterior que el destino actual.|
|**$<**|Archivo dependiente con una marca de tiempo posterior que el destino actual. Válido únicamente en comandos en las reglas de inferencia.|

Para especificar parte de una macro predefinida de nombre de archivo, anexar un modificador de macro y entre paréntesis la macro modificada.

|Modificador|Parte de nombre de archivo resultante|
|--------------|-----------------------------|
|**D**|Unidad más directorio|
|**B**|Nombre base|
|**F**|Nombre base y la extensión|
|**R**|Unidad más directorio más nombre base|

## <a name="see-also"></a>Vea también

[Macros NMAKE especiales](../build/special-nmake-macros.md)
