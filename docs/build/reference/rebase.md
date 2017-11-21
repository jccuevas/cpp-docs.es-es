---
title: -REBASE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /rebase
dev_langs: C++
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 05b718b20ad941764158f2de461614885b0627fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="rebase"></a>/REBASE
```  
/REBASE[:modifiers]  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción establece las direcciones base para los archivos especificados. EDITBIN asigna nuevas direcciones base en un espacio de direcciones contiguas en función del tamaño de cada archivo redondeado a lo 64 KB más próximos. Para obtener más información acerca de las direcciones base, vea la [dirección Base](../../build/reference/base-base-address.md) (/ BASE) del vinculador.  
  
 Especifique los archivos ejecutables y DLL en el programa la *archivos* argumento en la línea de comandos EDITBIN en el orden en el que se basará. También puede especificar uno o varios *modificadores*, separados por punto y coma (**,**):  
  
|Modificador|Acción|  
|--------------|------------|  
|BASE de**=***dirección*|Proporciona una dirección inicial para reasignar direcciones base a los archivos. Especifique *dirección* en formato decimal o notación del lenguaje c.. Si no se especifica BASE, la dirección base inicial predeterminada es 0 x 400000. Debe especificarse si inferior se usa, BASE, y *dirección* establece el final del intervalo de direcciones base.|  
|BASEFILE|Crea un archivo denominado COFFBASE. TXT, que es un archivo de texto en el formato esperado por del vínculo/opción de BASE.|  
|ABAJO|Hace que EDITBIN reasigne las direcciones base hacia abajo desde una dirección final. Los archivos se vuelven a asignar en el orden especificado, con el primer archivo que se encuentra en la dirección más alta posible bajo el final del intervalo de direcciones. BASE debe usarse con abajo para asegurarse de suficiente espacio de direcciones para basar los archivos. Para determinar el espacio de dirección necesario para los archivos especificados, ejecute EDITBIN con la opción /REBASE en los archivos y agregue 64 KB al tamaño total mostrado.|  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)