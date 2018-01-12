---
title: Las herramientas del vinculador LNK4221 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4221
dev_langs: C++
helpviewer_keywords: LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3fb348ebb05b7af40821b4f3968a920c2e9e773
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4221"></a>Advertencia de las herramientas del vinculador LNK4221
Este archivo de objeto no define los símbolos públicos previamente definidos, por lo que no se utilizará por cualquier operación de enlace que utiliza esta biblioteca  
  
 Tenga en cuenta los siguientes fragmentos de código de dos.  
  
```  
// a.cpp  
#include <atlbase.h>  
```  
  
```  
// b.cpp  
#include <atlbase.h>  
int function()  
{  
   return 0;  
}  
  
```  
  
 Para compilar los archivos y crear dos archivos de objeto, ejecute **cl /c a.cpp b.cpp** en un símbolo del sistema. Si vincula los archivos objeto ejecutando **vincular/lib out a.obj b.obj**, recibirá la advertencia LNK4221. Si vincula los objetos ejecutando **vincular/lib out b.obj a.obj**, no recibirá una advertencia.  
  
 Dado que el vinculador funciona de una manera de último en entrar en salir (LIFO), se genera ninguna advertencia en el segundo escenario. En el primer escenario, b.obj se procesa antes que a.obj y a.obj no tiene ningún nuevo símbolo que agregar. Si indica al vinculador que procese a.obj en primer lugar, puede evitar la advertencia.  
  
 Una causa común de este error es cuando dos archivos de origen especifican la opción [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md) con el mismo nombre de archivo de encabezado especificado en el **encabezado precompilado** campo. Una causa común de este problema afecta a stdafx.h ya que, de forma predeterminada, stdafx.cpp incluye stdafx.h y no agrega ningún nuevo símbolo. Si otro archivo de código fuente incluye stdafx.h con **/Yc** y el archivo .obj asociado se procesa antes que stdafx.obj, el vinculador producirá LNK4221.  
  
 Una manera de resolver este problema es asegurarse de que para cada encabezado precompilado, hay solo un archivo de origen que se incluye con **/Yc**. Todos los demás archivos de origen deben utilizar encabezados precompilados. Para obtener más información sobre cómo cambiar esta configuración, consulte [/Yu (utilizar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md).