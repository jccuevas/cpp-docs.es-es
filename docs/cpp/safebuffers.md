---
title: "safebuffers | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "safebuffers"
  - "safebuffers_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) (C++), safebuffers"
  - "safebuffers __declspec (palabra clave)"
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# safebuffers
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Indica al compilador que no inserte comprobaciones de seguridad de saturación del búfer para una función.  
  
## Sintaxis  
  
```  
__declspec( safebuffers )  
```  
  
## Comentarios  
 La opción del compilador **\/GS** hace que el compilador compruebe las saturaciones del búfer mediante la inserción de comprobaciones de seguridad en la pila.  Los tipos de estructuras de datos que son aptos para las comprobaciones de seguridad se describen en [\/GS \(Comprobación de seguridad del búfer\)](../build/reference/gs-buffer-security-check.md).  Para obtener más información sobre la detección de saturación del búfer, vea [Comprobación de seguridad exhaustiva del compilador](http://go.microsoft.com/fwlink/?linkid=7260) en el sitio web de MSDN.  
  
 Un análisis manual externo o realizado por un experto para revisar el código puede determinar si una función está protegida de la saturación del búfer.  En ese caso, se pueden suprimir las comprobaciones de seguridad de una función mediante la aplicación de la palabra clave \_\_`declspec(safebuffers)` en la declaración de función.  
  
> [!CAUTION]
>  Las comprobaciones de seguridad del búfer proporcionan una protección de seguridad importante y apenas repercuten en el rendimiento.  Por tanto, se recomienda que no las suprima, excepto en el caso poco frecuente de que el rendimiento de una función tenga una importancia crítica y se sepa que la función está segura.  
  
## Funciones insertadas  
 Una *función principal* puede utilizar una palabra clave [inlining](../misc/inline-inline-forceinline.md) para insertar una copia de una *función secundaria*.  Si la palabra clave \_\_`declspec(safebuffers)` se aplica a una función, la detección de saturación del búfer se suprime para esa función.  Sin embargo, inlining afecta a la palabra clave \_\_`declspec(safebuffers)` de las maneras siguientes.  
  
 Supongamos que la opción del compilador **\/GS** está especificada para ambas funciones pero la función principal especifica la palabra clave \_\_`declspec(safebuffers)` .  Las estructuras de datos en la función secundaria hacen que sea apta para las comprobaciones de seguridad, y la función no suprime dichas comprobaciones.  En este caso:  
  
-   Especifique la palabra clave [\_\_forceinline](../misc/inline-inline-forceinline.md) en la función secundaria para hacer que el compilador inserte esa función independientemente de las optimizaciones del compilador.  
  
-   Dado que la función secundaria es apta para las comprobaciones de seguridad, las comprobaciones de seguridad también se aplican a la función principal, aunque especifique la palabra clave \_\_`declspec(safebuffers)` .  
  
## Ejemplo  
 En el código siguiente se muestra cómo se puede usar la palabra clave \_\_`declspec(safebuffers)` .  
  
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
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [inline, \_\_inline, \_\_forceinline](../misc/inline-inline-forceinline.md)   
 [strict\_gs\_check](../preprocessor/strict-gs-check.md)