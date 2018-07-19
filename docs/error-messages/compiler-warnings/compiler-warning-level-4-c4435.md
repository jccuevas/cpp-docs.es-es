---
title: Compilador advertencia (nivel 4) C4435 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72c29bd6d9ffdb4eabb036c61d85a6572cef8fe2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293941"
---
# <a name="compiler-warning-level-4-c4435"></a>Advertencia del compilador (nivel 4) C4435
'clase1': La distribución de objetos de /vd2 cambiará debido a la base virtual 'clase2'  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
 En el valor predeterminado la opción de/vd1 de compilación, la clase derivada no tiene un `vtordisp` campo para la base virtual indicada.  Si/vd2 o `#pragma vtordisp(2)` está en vigor, un `vtordisp` campo estará presente, cambiar el diseño del objeto.  Esto puede causar problemas de compatibilidad binaria si interactivas módulos se compilan con diferentes `vtordisp` configuración.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4435.  
  
```cpp  
// C4435.cpp  
// compile with: /c /W4  
#pragma warning(default : 4435)  
class A  
{  
public:  
    virtual ~A() {}  
};  
  
class B : public virtual A  // C4435  
{};  
```  
  
## <a name="see-also"></a>Vea también  
 [vtordisp](../../preprocessor/vtordisp.md)   
 [/vd (Deshabilitar desplazamientos de constructores)](../../build/reference/vd-disable-construction-displacements.md)