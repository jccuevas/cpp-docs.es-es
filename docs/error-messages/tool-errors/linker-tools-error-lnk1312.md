---
title: Las herramientas del vinculador LNK1312 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1312
dev_langs:
- C++
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d7f7b57512f58402403a50bf57176f975769573
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1312"></a>Error de las herramientas del vinculador LNK1312
archivo no válido o dañado: no se puede importar el ensamblado  
  
 Al compilar un ensamblado, un archivo que no sea un módulo o ensamblado compilado con **/CLR** se pasó a la **/ASSEMBLYMODULE** opción del vinculador.  Si se pasa a un archivo de objeto para **/ASSEMBLYMODULE**, simplemente pase el objeto directamente al vinculador, en lugar de al **/ASSEMBLYMODULE**.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente crea el archivo .obj.  
  
```  
// LNK1312.cpp  
// compile with: /clr /LD  
public ref class A {  
public:  
   int i;  
};  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error LNK1312.  
  
```  
// LNK1312_b.cpp  
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj  
// LNK1312 error expected  
public ref class M {};  
```