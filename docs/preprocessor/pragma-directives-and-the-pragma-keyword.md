---
title: Directivas pragma y la palabra clave __Pragma | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#pragma'
dev_langs:
- C++
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ccc6ab8fe90b8b97dee213d65e19eb903249da6
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="pragma-directives-and-the-pragma-keyword"></a>Directives pragma y la palabra clave __pragma
Las directivas pragma especifican características del compilador específicas del equipo o del funcionamiento. La palabra clave `__pragma`, que es específica del compilador de Microsoft, permite la codificación de directivas pragma dentro de definiciones de macro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      #pragma token-string  
__pragma(token-string)  
```  
  
## <a name="remarks"></a>Comentarios  
 Cada implementación de C y C++ admite algunas características exclusivas del equipo host o del sistema operativo. Algunos programas, por ejemplo, deben realizar el control preciso sobre las áreas de memoria donde se colocan los datos o controlar la manera en que determinadas funciones reciben los parámetros. Las directivas `#pragma` proporcionan un método para que cada compilador ofrezca características específicas del equipo o del sistema operativo a la vez que conservan la compatibilidad total con los lenguajes C y C++.  
  
 Las pragmas son específicas del equipo o del sistema operativo específico por definición, y normalmente son diferentes para cada compilador. Las pragmas se pueden utilizar en instrucciones condicionales, para proporcionar nueva funcionalidad de preprocesador, o para proporcionar información que se define en la implementación al compilador.  
  
 `token-string` es una serie de caracteres que proporcionan instrucciones del compilador y argumentos concretos, si los hay. El signo de número (**#**) debe ser el primer carácter no sea un espacio en blanco en la línea que contiene la directiva pragma; los caracteres de espacio en blanco pueden separar el signo de número y la palabra "pragma". A continuación de `#pragma`, se ha de escribir el texto que el traductor pueda analizar como tokens de preprocesamiento. El argumento para `#pragma` está sujeto a la expansión de macro.  
  
 Si el compilador encuentra una pragma que no reconoce, emite una advertencia y continúa la compilación.  
  
 Los compiladores de Microsoft C y C++ reconocen las pragmas siguientes:  
  
||||  
|-|-|-|  
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|  
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[comment](../preprocessor/comment-c-cpp.md)|  
|[component](../preprocessor/component.md)|[conform](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|  
|[data_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|  
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|  
|[function](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|  
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|  
|[intrinsic](../preprocessor/intrinsic.md)|[bucle](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|  
|[managed](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)||  
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||  
|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|  
|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|[region, endregion](../preprocessor/region-endregion.md)|  
|[runtime_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|  
|[strict_gs_check](../preprocessor/strict-gs-check.md)|[unmanaged](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|  
|[warning](../preprocessor/warning.md)|||  
  
 1. Solo la admite el compilador de C++.  
  
## <a name="pragmas-and-compiler-options"></a>Pragmas y opciones del compilador  
 Algunas pragmas proporcionan la misma funcionalidad que las opciones del compilador. Cuando una pragma se encuentra en el código fuente, invalida el comportamiento especificado por la opción del compilador. Por ejemplo, si especificó [/zp8](../build/reference/zp-struct-member-alignment.md), puede reemplazar esta configuración de compilador para secciones específicas del código con [pack](../preprocessor/pack.md):  
  
```  
cl /Zp8 ...  
  
<file> - packing is 8  
// ...  
#pragma pack(push, 1) - packing is now 1  
// ...  
#pragma pack(pop) - packing is 8  
</file>  
```  
  
## <a name="the-pragma-keyword"></a>La palabra clave __pragma()  
 **Específicos de Microsoft**  
  
 El compilador también admite la palabra clave `__pragma`, que tiene la misma funcionalidad que la directiva `#pragma`, pero puede utilizarse alineada en una definición de macro. El `#pragma` directiva no se puede usar en una definición de macro porque el compilador interpreta el carácter de signo de número ('#') en la directiva como la [operador de generación de cadenas (#)](../preprocessor/stringizing-operator-hash.md).  
  
 En el siguiente ejemplo de código se muestra cómo se puede utilizar la palabra clave `__pragma` en una macro. Este código se ha extraído del encabezado mfcdual.h del ejemplo ACDUAL en "Ejemplos de compatibilidad COM del compilador":  
  
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
  
 **Fin de específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Referencia del preprocesador de C/c ++](../preprocessor/c-cpp-preprocessor-reference.md)   
 [Pragmas de C](../c-language/c-pragmas.md)   
 [Palabras clave](../cpp/keywords-cpp.md)