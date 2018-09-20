---
title: Consejos sobre la programación general MBCS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc27d0b0396fed6e6b03f6c3f8e1f2332fcceecf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421107"
---
# <a name="general-mbcs-programming-advice"></a>Consejos generales sobre la programación con MBCS

Use las sugerencias siguientes:

- Para mayor flexibilidad, use las macros de tiempo de ejecución como `_tcschr` y `_tcscpy` cuando sea posible. Para obtener más información, consulte [asignaciones de texto genérico en Tchar.h](../text/generic-text-mappings-in-tchar-h.md).

- Utilice el tiempo de ejecución de C `_getmbcp` función para obtener información acerca de la página de códigos actual.

- No reutilice los recursos de cadena. Dependiendo del lenguaje de destino, una cadena determinada podría tener un significado diferente cuando se traduce. Por ejemplo, el menú principal de "Archivo" en la aplicación podría traducir de forma diferente de la cadena "File" en un cuadro de diálogo. Si necesita usar más de una cadena con el mismo nombre, utilice identificadores diferentes para cada uno.

- Es posible que desee averiguar si la aplicación se está ejecutando en un sistema operativo habilitado para MBCS. Para ello, establezca una marca al inicio del programa; No confíe en las llamadas de API.

- Al diseñar los cuadros de diálogo, permitir aproximadamente un 30% espacio adicional al final de los controles de texto estático para la traducción de MBCS.

- Tenga cuidado al seleccionar fuentes para la aplicación, ya que algunas fuentes no están disponibles en todos los sistemas.

- Al seleccionar la fuente para los cuadros de diálogo, utilice [MS Shell Dlg](/windows/desktop/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) en lugar de MS Sans Serif o Helvetica. MS Shell Dlg se reemplaza por la fuente correcta por el sistema antes de crear el cuadro de diálogo. Uso de MS Shell Dlg garantiza que los cambios en el sistema operativo para tratar con esta fuente estarán disponibles automáticamente. (MFC reemplaza MS Shell Dlg por DEFAULT_GUI_FONT o la fuente del sistema en Windows 95, Windows 98 y Windows NT 4 porque estos sistemas no controlan MS Shell Dlg correctamente.)

- Al diseñar la aplicación, decidir las cadenas que se pueden localizar. En caso de duda, se supone que se traducirá cualquier cadena determinada. Por lo tanto, no mezcle las cadenas que se pueden localizar con las que no.

## <a name="see-also"></a>Vea también

[Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)<br/>
[Aumento y disminución de punteros](../text/incrementing-and-decrementing-pointers.md)