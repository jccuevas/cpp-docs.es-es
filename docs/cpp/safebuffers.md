---
title: safebuffers | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- safebuffers_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: ceb7d5796002bd54055b74d56a136706890494c4
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="safebuffers"></a>safebuffers
**Específicos de Microsoft**  
  
 Indica al compilador que no inserte comprobaciones de seguridad de saturación del búfer para una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec( safebuffers )  
```  
  
## <a name="remarks"></a>Comentarios  
 El **/GS** opción del compilador hace que el compilador comprobar las saturaciones de búfer mediante la inserción de comprobaciones de seguridad en la pila. Los tipos de estructuras de datos que son aptas para la comprobación de seguridad se describen en [/GS (comprobación de seguridad de búfer)](../build/reference/gs-buffer-security-check.md). Para obtener más información acerca de la detección de saturación del búfer, vea [compilador Security Checks In Depth](http://go.microsoft.com/fwlink/?linkid=7260) en el sitio Web de MSDN.  
  
 Un análisis manual externo o realizado por un experto para revisar el código puede determinar si una función está protegida de la saturación del búfer. En ese caso, puede suprimir las comprobaciones de seguridad para una función aplicando el `__declspec(safebuffers)` palabra clave para la declaración de función.  
  
> [!CAUTION]
>  Las comprobaciones de seguridad del búfer proporcionan una protección de seguridad importante y apenas repercuten en el rendimiento. Por tanto, se recomienda que no las suprima, excepto en el caso poco frecuente de que el rendimiento de una función tenga una importancia crítica y se sepa que la función está segura.  
  
## <a name="inline-functions"></a>Funciones insertadas  
 A *función principal* puede usar un [inclusión](inline-functions-cpp.md) palabra clave que se va a insertar una copia de un *función secundaria*. Si el `__declspec(safebuffers)` palabra clave se aplica a una función, detección de saturación del búfer se suprime para esa función. Sin embargo, inlining afecta a la `__declspec(safebuffers)` palabra clave de las maneras siguientes.  
  
 Suponga que el **/GS** se especifica la opción de compilador para ambas funciones, pero la función principal especifica la `__declspec(safebuffers)` palabra clave. Las estructuras de datos en la función secundaria hacen que sea apta para las comprobaciones de seguridad, y la función no suprime dichas comprobaciones. En este caso:  
  
-   Especifique el [__forceinline](inline-functions-cpp.md) palabra clave en la función secundaria para hacer que el compilador inserte esa función independientemente de las optimizaciones del compilador.  
  
-   Dado que la función secundaria es apta para las comprobaciones de seguridad, comprobaciones de seguridad también se aplican a la función principal, aunque especifique el `__declspec(safebuffers)` palabra clave.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo utilizar el `__declspec(safebuffers)` palabra clave.  
  
```  
// compile with: /c /GS  
typedef struct {  
    int x[20];  
} BUFFER;  
static int checkBuffers() {  
    BUFFER cb;  
    // Use the buffer...  
    return 0;  
};  
static __declspec(safebuffers)   
    int noCheckBuffers() {  
    BUFFER ncb;  
    // Use the buffer...  
    return 0;  
}  
int wmain() {  
    checkBuffers();  
    noCheckBuffers();  
    return 0;  
}  
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [inline, __inline, \__forceinline](inline-functions-cpp.md)   
 [strict_gs_check](../preprocessor/strict-gs-check.md)
