---
title: Consejos generales sobre la programación con MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 887387220105614eb3257f008ec601a6fc0adc18
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491185"
---
# <a name="general-mbcs-programming-advice"></a>Consejos generales sobre la programación con MBCS

Use las sugerencias siguientes:

- Para mayor flexibilidad, utilice macros en tiempo de ejecución `_tcschr` como `_tcscpy` y cuando sea posible. Para obtener más información, vea [asignaciones de texto genérico en TCHAR. h](../text/generic-text-mappings-in-tchar-h.md).

- Utilice la función en tiempo `_getmbcp` de ejecución de C para obtener información acerca de la página de códigos actual.

- No reutilice los recursos de cadena. Dependiendo del lenguaje de destino, una cadena determinada podría tener un significado diferente cuando se traduzca. Por ejemplo, "archivo" en el menú principal de la aplicación puede convertirse de forma diferente de la cadena "archivo" en un cuadro de diálogo. Si necesita usar más de una cadena con el mismo nombre, use identificadores de cadena diferentes para cada una de ellas.

- Es posible que desee averiguar si la aplicación se ejecuta en un sistema operativo habilitado para MBCS. Para ello, establezca una marca al inicio del programa; no se base en las llamadas API.

- Al diseñar cuadros de diálogo, permita aproximadamente un 30% de espacio adicional al final de los controles de texto estático para la traducción de MBCS.

- Tenga cuidado al seleccionar las fuentes de la aplicación, ya que algunas fuentes no están disponibles en todos los sistemas.

- Al seleccionar la fuente para los cuadros de diálogo, use [MS Shell Dlg](/windows/win32/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) en lugar de MS Sans Serif o Helvetica. MS Shell Dlg se reemplaza con la fuente correcta del sistema antes de crear el cuadro de diálogo. El uso de MS Shell Dlg garantiza que los cambios en el sistema operativo para tratar esta fuente estarán disponibles automáticamente. (MFC reemplaza a MS Shell Dlg con DEFAULT_GUI_FONT o la fuente del sistema en Windows 95, Windows 98 y Windows NT 4 porque esos sistemas no controlan correctamente MS Shell Dlg).

- Al diseñar la aplicación, decida qué cadenas se pueden localizar. En caso de duda, supongamos que se localizará cualquier cadena determinada. Como tal, no mezcle cadenas que se puedan localizar con aquellas que no puedan.

## <a name="see-also"></a>Vea también

[Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)<br/>
[Aumento y disminución de punteros](../text/incrementing-and-decrementing-pointers.md)
