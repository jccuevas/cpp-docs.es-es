---
title: "Advertencia de las herramientas del vinculador LNK4221 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4221"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4221"
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4221
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este archivo de objeto no define ningún símbolo público que no se haya definido previamente, por lo que no se usará en ninguna vinculación que utilice esta biblioteca  
  
 Considere los dos fragmentos de código siguientes.  
  
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
  
 Para compilar los archivos y crear dos archivos objeto, ejecute **cl \/c a.cpp b.cpp** en un símbolo del sistema.  Si vincula los archivos objeto ejecutando **link \/lib \/out:test.lib a.obj b.obj**, recibirá la advertencia LNK4221.  Si vincula los objetos ejecutando **link \/lib \/out:test.lib b.obj a.obj**, no recibirá ninguna advertencia.  
  
 En el segundo caso no se genera ninguna advertencia porque el vinculador funciona con un método LIFO \(último en entrar, primero en salir\).  En el primer escenario, b.obj se procesa antes que a.obj y a.obj no tiene ningún nuevo símbolo que agregar.  Si indica al vinculador que procese a.obj en primer lugar, puede evitar la advertencia.  
  
 Una causa habitual de este error es que dos archivos de código fuente especifiquen la opción [\/Yc \(Crear archivo de encabezado precompilado\)](../../build/reference/yc-create-precompiled-header-file.md) con el mismo nombre de archivo de encabezado especificado en el campo **Encabezado precompilado**.  Otra causa habitual de este problema tiene que ver con stdafx.h ya que, de forma predeterminada, stdafx.cpp incluye stdafx.h y no agrega ningún nuevo símbolo.  Si otro archivo de código fuente incluye stdafx.h con **\/Yc** y el archivo .obj asociado se procesa antes que stdafx.obj, el vinculador producirá LNK4221.  
  
 Una manera de resolver este problema es asegurarse de que para cada encabezado precompilado, hay solo un archivo de código fuente que lo incluye con **\/Yc**.  Todos los demás archivos de código fuente deben utilizar encabezados precompilados.  Para obtener más información sobre cómo cambiar esta configuración, vea [\/Yu \(Utilizar el archivo de encabezado precompilado\)](../../build/reference/yu-use-precompiled-header-file.md).