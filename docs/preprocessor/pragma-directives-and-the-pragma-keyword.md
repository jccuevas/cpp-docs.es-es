---
title: "Directives pragma y la palabra clave __pragma | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#pragma"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "#pragma (directivas), C/C++"
  - "__pragma (palabra clave)"
  - "directivas pragma (#pragma)"
  - "pragma (directivas), C/C++"
  - "pragma (directivas)"
  - "pragma (directivas), C/C++"
  - "preprocesador"
  - "preprocesador, pragma (directivas)"
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# Directives pragma y la palabra clave __pragma
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las directivas pragma especifican características del compilador específicas del equipo o del funcionamiento.  La palabra clave `__pragma`, que es específica del compilador de Microsoft, permite la codificación de directivas pragma dentro de definiciones de macro.  
  
## Sintaxis  
  
```  
  
      #pragma token-string  
__pragma(token-string)  
```  
  
## Comentarios  
 Cada implementación de C y C\+\+ admite algunas características exclusivas del equipo host o del sistema operativo.  Algunos programas, por ejemplo, deben realizar el control preciso sobre las áreas de memoria donde se colocan los datos o controlar la manera en que determinadas funciones reciben los parámetros.  Las directivas `#pragma` proporcionan un método para que cada compilador ofrezca características específicas del equipo o del sistema operativo a la vez que conservan la compatibilidad total con los lenguajes C y C\+\+.  
  
 Las pragmas son específicas del equipo o del sistema operativo específico por definición, y normalmente son diferentes para cada compilador.  Las pragmas se pueden utilizar en instrucciones condicionales, para proporcionar nueva funcionalidad de preprocesador, o para proporcionar información que se define en la implementación al compilador.  
  
 `token-string` es una serie de caracteres que proporcionan instrucciones del compilador y argumentos concretos, si los hay.  El signo de número \(**\#**\) debe ser el primer carácter que no es un espacio en blanco de la línea que contiene la pragma; los caracteres de espacio en blanco pueden separar el signo de número y la palabra "pragma".  A continuación de `#pragma`, se ha de escribir el texto que el traductor pueda analizar como tokens de preprocesamiento.  El argumento para `#pragma` está sujeto a la expansión de macro.  
  
 Si el compilador encuentra una pragma que no reconoce, emite una advertencia y continúa la compilación.  
  
 Los compiladores de Microsoft C y C\+\+ reconocen las pragmas siguientes:  
  
||||  
|-|-|-|  
|[alloc\_text](../preprocessor/alloc-text.md)|[auto\_inline](../preprocessor/auto-inline.md)|[bss\_seg](../preprocessor/bss-seg.md)|  
|[check\_stack](../preprocessor/check-stack.md)|[code\_seg](../preprocessor/code-seg.md)|[comment](../preprocessor/comment-c-cpp.md)|  
|[component](../preprocessor/component.md)|[conform](../preprocessor/conform.md) <sup>1</sup>|[const\_seg](../preprocessor/const-seg.md)|  
|[data\_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect\_mismatch](../preprocessor/detect-mismatch.md)|  
|[fenv\_access](../preprocessor/fenv-access.md)|[float\_control](../preprocessor/float-control.md)|[fp\_contract](../preprocessor/fp-contract.md)|  
|[function](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include\_alias](../preprocessor/include-alias.md)|  
|[init\_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline\_depth](../preprocessor/inline-depth.md)|[inline\_recursion](../preprocessor/inline-recursion.md)|  
|[intrinsic](../preprocessor/intrinsic.md)|[loop](../preprocessor/loop.md) <sup>1</sup>|[make\_public](../preprocessor/make-public.md)|  
|[managed](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)||  
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||  
|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|[pointers\_to\_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|  
|[pop\_macro](../preprocessor/pop-macro.md)|[push\_macro](../preprocessor/push-macro.md)|[region, endregion](../preprocessor/region-endregion.md)|  
|[runtime\_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|  
|[strict\_gs\_check](../preprocessor/strict-gs-check.md)|[unmanaged](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|  
|[warning](../preprocessor/warning.md)|||  
  
 1.  Solo la admite el compilador de C\+\+.  
  
## Pragmas y opciones del compilador  
 Algunas pragmas proporcionan la misma funcionalidad que las opciones del compilador.  Cuando una pragma se encuentra en el código fuente, invalida el comportamiento especificado por la opción del compilador.  Por ejemplo, si se ha especificado [\/Zp8](../build/reference/zp-struct-member-alignment.md), se puede reemplazar esta configuración del compilador para secciones específicas del código con [pack](../preprocessor/pack.md):  
  
```  
cl /Zp8 ...  
  
<file> - packing is 8  
// ...  
#pragma pack(push, 1) - packing is now 1  
// ...  
#pragma pack(pop) - packing is 8  
</file>  
```  
  
## La palabra clave \_\_pragma\(\)  
 **Específicos de Microsoft**  
  
 El compilador también admite la palabra clave `__pragma`, que tiene la misma funcionalidad que la directiva `#pragma`, pero puede utilizarse alineada en una definición de macro.  La directiva `#pragma` no se puede utilizar en una definición de macro porque el compilador interpreta el carácter de signo de número \("\#"\) en la directiva como [operador de generación de cadenas \(\#\)](../preprocessor/stringizing-operator-hash.md).  
  
 En el siguiente ejemplo de código se muestra cómo se puede utilizar la palabra clave `__pragma` en una macro.  Este código se ha extraído del encabezado mfcdual.h del ejemplo ACDUAL en "Ejemplos de compatibilidad COM del compilador":  
  
```  
#define CATCH_ALL_DUAL \  
CATCH(COleException, e) \  
{ \  
_hr = e->m_sc; \  
} \  
AND_CATCH_ALL(e) \  
{ \  
__pragma(warning(push)) \  
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \  
AFX_MANAGE_STATE(pThis->m_pModuleState); \  
__pragma(warning(pop)) \  
_hr = DualHandleException(_riidSource, e); \  
} \  
END_CATCH_ALL \  
return _hr; \  
```  
  
 **Fin de Específicos de Microsoft**  
  
## Vea también  
 [Referencia del preprocesador de C\/C\+\+](../preprocessor/c-cpp-preprocessor-reference.md)   
 [Pragmas de C](../c-language/c-pragmas.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)