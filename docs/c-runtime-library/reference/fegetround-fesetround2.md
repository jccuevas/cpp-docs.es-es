---
title: "fegetround, fesetround | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fegetround"
  - "fesetround"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fegetround"
  - "fesetround"
  - "fenv/fegetround"
  - "fenv/fesetround"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fegetround (función)"
  - "fesetround (función)"
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fegetround, fesetround
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene o establece el modo de redondeo de punto flotante actual.  
  
## Sintaxis  
  
```  
int fegetround(void);  
  
int fesetround(  
   int round_mode  
);   
```  
  
#### Parámetros  
 `round_mode`  
 El modo de redondeo que se va a establecer, como una de las macros de redondeo de punto flotante. Si el valor no es igual a una de las macros de redondeo de punto flotante, no se cambiará el modo de redondeo.  
  
## Valor devuelto  
 Si se realiza correctamente, `fegetround` devuelve el modo de redondeo como uno de los valores de la macro de redondeo de punto flotante. Devuelve un valor negativo si no se puede determinar el modo de redondeo actual.  
  
 Si se realiza correctamente, `fesetround` devuelve 0. De lo contrario, devuelve un valor distinto de cero.  
  
## Comentarios  
 Las operaciones de punto flotante pueden usar uno de los distintos modos de redondeo. Estos controlan en qué dirección se redondean los resultados de las operaciones de punto flotante cuando se almacenan los resultados. Estos son los nombres y los comportamientos de las macros de redondeo de punto flotante definidas en \<fenv.h\>:  
  
|Macro|Descripción|  
|-----------|-----------------|  
|FE\_DOWNWARD|Redondeo a infinito negativo.|  
|FE\_TONEAREST|Redondeo al más próximo.|  
|FE\_TOWARDZERO|Redondeo a cero.|  
|FE\_UPWARD|Redondeo a infinito positivo.|  
  
 El comportamiento predeterminado de FE\_TONEAREST es redondear los resultados que se encuentran entre valores representables al valor más próximo con un bit menos significativo par \(0\).  
  
 El modo de redondeo actual afecta a estas operaciones:  
  
-   Las conversiones de cadenas.  
  
-   Los resultados de los operadores aritméticos de punto flotante fuera de las expresiones constantes.  
  
-   Las funciones de redondeo de la biblioteca, como `rint` y `nearbyint`.  
  
-   Los valores devueltos de las funciones matemáticas de la biblioteca estándar.  
  
 El modo de redondeo actual no afecta a estas operaciones:  
  
-   Las funciones de la biblioteca `trunc`, `ceil`, `floor` y `lround`.  
  
-   Las conversiones implícitas de punto flotante a entero, que siempre se redondean a cero.  
  
-   Los resultados de los operadores aritméticos de punto flotante en expresiones constantes, que siempre se redondean al valor más cercano.  
  
 Para usar estas funciones, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv\_access](../../preprocessor/fenv-access.md).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`fegetround`, `fesetround`|\<fenv.h\>|\<cfenv\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [nearbyint, nearbyintf, nearbyintl](../../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)   
 [rint, rintf, rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)   
 [lrint, lrintf, lrintl, llrint, llrintf, llrintl](../../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)