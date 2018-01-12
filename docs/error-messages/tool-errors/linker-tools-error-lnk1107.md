---
title: Las herramientas del vinculador LNK1107 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1107
dev_langs: C++
helpviewer_keywords: LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fae412de31163aa1b5248af43227042cd04563ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1107"></a>Error de las herramientas del vinculador LNK1107
archivo no válido o dañado: no se puede leer en ubicación  
  
 La herramienta no pudo leer el archivo. Vuelva a crear el archivo.  
  
 LNK1107 también se puede producir si intenta pasar un módulo (extensión de archivo .dll o .netmodule creada con [/CLR: noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) o [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)) al vinculador; pasa el archivo .obj en su lugar.  
  
 Si compila el ejemplo siguiente:  
  
```  
// LNK1107.cpp  
// compile with: /clr /LD  
public ref class MyClass {  
public:  
   void Test(){}  
};  
```  
  
 y, a continuación, especifique **vincular LNK1107.dll** en la línea de comandos, obtendrá LNK1107.  Para resolver el error, especifique **vincular LNK1107.obj** en su lugar.