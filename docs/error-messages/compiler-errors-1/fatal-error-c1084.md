---
title: Error irrecuperable C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: 649686857000b2bee469f0e3ec551d49717c1d7b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204079"
---
# <a name="fatal-error-c1084"></a>Error irrecuperable C1084

No se puede leer el archivo filetype: ' file ': mensaje

Este error suele deberse a un error en una llamada API del sistema interno realizada por el compilador. El mensaje que se muestra cuando se encuentra este error suele generarse mediante [_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) o [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage).

Con los siguientes pasos, puede que resulte más fácil resolver C1084:

- Compruebe que el archivo especificado existe.

- Compruebe que están establecidos los permisos adecuados para acceder al archivo especificado.

- Asegúrese de que la sintaxis de línea de comandos se ajusta a las reglas descritas en [Sintaxis de línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md).

- Asegúrese de que las variables de entorno **TMP** y **temp** estén establecidas correctamente, así como los permisos adecuados para obtener acceso a los directorios a los que hacen referencia estas variables de entorno. Asegúrese también de que las unidades a las que hacen referencia las variables de entorno **TMP** y **temp** contengan una cantidad adecuada de espacio disponible.

- Si en el mensaje se indica “número de archivo incorrecto”, puede que el archivo especificado se estuviera cerrando en primer plano mientras se compilaba en segundo plano.

Después de llevar a cabo los diagnósticos anteriores, realice una compilación limpia.
