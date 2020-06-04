---
title: /REBASE
ms.date: 11/04/2016
f1_keywords:
- /rebase
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
ms.openlocfilehash: 42cbcb911fcd0aa7753d84aae5523d28371b9972
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319205"
---
# <a name="rebase"></a>/REBASE

```
/REBASE[:modifiers]
```

## <a name="remarks"></a>Comentarios

Esta opción establece las direcciones base para los archivos especificados. EDITBIN asigna nuevas direcciones bases en un espacio de direcciones contiguo según el tamaño de cada archivo redondeado a los 64 KB más cercano. Para obtener más información sobre las direcciones bases, vea la [dirección Base](base-base-address.md) (/ BASE) del vinculador.

Especifique los archivos ejecutables y DLL en el programa la *archivos* argumento en la línea de comandos EDITBIN en el orden en que basarse. Opcionalmente, puede especificar uno o varios *modificadores*, separados por punto y coma (**,**):

|Modificador|Acción|
|--------------|------------|
|**BASE=**<em>address</em>|Proporciona una dirección inicial para reasignar las direcciones base para los archivos. Especificar *dirección* en notación de lenguaje de C o decimal. Si no se especifica la BASE, la dirección base de inicio predeterminada es 0 x 400000. Debe especificarse si inferior se usa, BASE, y *dirección* establece el final del intervalo de direcciones base.|
|**BASEFILE**|Crea un archivo denominado COFFBASE. TXT, que es un archivo de texto en el formato esperado por el del vínculo/opción de BASE.|
|**ABAJO**|Hace que EDITBIN reasigne las direcciones base hacia abajo desde una dirección final. Los archivos se vuelven a asignar en el orden especificado, con el primer archivo que se encuentra en la dirección más alta posible bajo el final del intervalo de direcciones. BASE debe utilizarse con profundidad para asegurarse de suficiente espacio de direcciones para basar los archivos. Para determinar el espacio de direcciones necesario para los archivos especificados, ejecute EDITBIN con /REBASE en los archivos y agregue 64 KB para el tamaño total mostrado.|

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](editbin-options.md)
