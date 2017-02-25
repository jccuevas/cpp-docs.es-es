---
title: "Compatibilidad con el punto flotante | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.math"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "números de punto flotante"
  - "números de punto flotante, rutinas matemáticas"
  - "rutinas matemáticas"
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Compatibilidad con el punto flotante
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muchas de las funciones de biblioteca en tiempo de ejecución de Microsoft requieren compatibilidad de punto flotante por parte de un coprocesador matemático o de las bibliotecas de punto flotante que acompañan al compilador.  Las funciones de compatibilidad de punto flotante se cargan únicamente si son necesarias.  
  
 Cuando se usa un especificador de tipo de punto flotante en la cadena de formato de una llamada a una función de la familia `printf` o `scanf`, se debe especificar un valor de punto flotante o un puntero a un valor de punto flotante en la lista de argumentos para indicar al compilador que es necesario admitir puntos flotantes.  
  
 Consulte [\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md) para ver código de ejemplo que muestre cómo controlar excepciones de punto flotante.  
  
 La precisión del punto flotante en los valores intermedios se controla por medio de las funciones [\_control87, \_controlfp, \_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md).  El control de precisión en `_controlfp` está establecido de forma predeterminada en 53 bits \(\_PC\_53\).  Si se vincula mediante FP10.OBJ, el control de precisión predeterminado cambia a 64 bits \(\_PC\_64\).  En la línea de comandos del vinculador, FP10.OBJ debe aparecer antes de LIBC.LIB, LIBCMT.LIB o MSVCRT.LIB.  
  
### Funciones de punto flotante  
  
|Rutina|Uso|Equivalente de .NET Framework|  
|------------|---------|-----------------------------------|  
|[abs](../Topic/abs.md)|Devolver el valor absoluto de `int`|[\<caps:sentence id\="tgt14" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[acos, acosf](../c-runtime-library/reference/acos-acosf-acosl.md)|Calcular el arco coseno|[\<caps:sentence id\="tgt17" sentenceid\="954a441495360a1fa8b0170297b2ff38" class\="tgtSentence"\>System::Math::Acos\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.acos.aspx)|  
|[asin, asinf](../c-runtime-library/reference/asin-asinf-asinl.md)|Calcular el arcoseno|[\<caps:sentence id\="tgt20" sentenceid\="313917cde9698a0924536719f5bece25" class\="tgtSentence"\>System::Math::Asin\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.asin.aspx)|  
|[atan, atanf, atan2, atan2f](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Calcular el arcotangente|[System::Math::Atan](https://msdn.microsoft.com/en-us/library/system.math.atan.aspx), [System::Math::Atan2](https://msdn.microsoft.com/en-us/library/system.math.atan2.aspx)|  
|[atof, \_atof\_l, \_wtof, \_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convertir la cadena de caracteres en un valor de punto flotante de precisión doble|[System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx), [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[Funciones Bessel](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Calcular las funciones Bessel `_j0`, `_j1`, `_jn`, `_y0`, `_y1`, `_yn`|No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_cabs](../c-runtime-library/reference/cabs.md)|Hallar el valor absoluto de un número complejo|No es aplicable.|  
|[cbrt](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|Calcular la raíz cúbica|No es aplicable.|  
|[ceil, ceilf](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Hallar el techo de un entero|[\<caps:sentence id\="tgt39" sentenceid\="656009d71fb974368bded363746de018" class\="tgtSentence"\>System::Math::Ceiling\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.ceiling.aspx)|  
|[\_chgsign, \_chgsignf, \_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|Invertir el signo de punto flotante de precisión doble o el argumento de punto flotante de precisión doble larga|No es aplicable.|  
|[\_clear87, \_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|Obtener y borrar la palabra de estado de punto flotante|No es aplicable.|  
|[\_control87, \_controlfp, \_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md), [\_controlfp\_s](../c-runtime-library/reference/controlfp-s.md)|Obtener la palabra de control de punto flotante anterior y definir el nuevo valor de palabra de control|No es aplicable.|  
|[copysign, copysignf, copysignl, \_copysign, \_copysignf, \_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|Devolver un valor con el signo de otro|No es aplicable.|  
|[cos, cosf, cosh, coshf](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|Calcular el coseno|[System::Math::Cos](https://msdn.microsoft.com/en-us/library/system.math.cos.aspx), [System::Math::Cosh](https://msdn.microsoft.com/en-us/library/system.math.cosh.aspx)|  
|[difftime](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Calcular la diferencia entre dos valores de hora especificados|[\<caps:sentence id\="tgt54" sentenceid\="5f4f365a3cd7f368db2f6ce31b797fdf" class\="tgtSentence"\>System::DateTime::Subtract\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)|  
|[div](../c-runtime-library/reference/div.md)|Dividir un entero entre otro, de lo cual se obtiene un cociente y un resto|No es aplicable.|  
|[\_ecvt](../c-runtime-library/reference/ecvt.md), [\_ecvt\_s](../c-runtime-library/reference/ecvt-s.md)|Convertir `double` en una cadena de caracteres de la longitud especificada|[\<caps:sentence id\="tgt60" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[exp, expf](../c-runtime-library/reference/exp-expf.md)|Calcular la función exponencial|[\<caps:sentence id\="tgt63" sentenceid\="81a65df6ac66cdc4a4b12c2f7e555487" class\="tgtSentence"\>System::Math::Exp\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.exp.aspx)|  
|[fabs, fabsf](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Hallar el valor absoluto|[\<caps:sentence id\="tgt66" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[\_fcvt](../c-runtime-library/reference/fcvt.md), [\_fcvt\_s](../c-runtime-library/reference/fcvt-s.md)|Convertir `double` en una cadena que tenga el número especificado de dígitos después del separador decimal|[\<caps:sentence id\="tgt69" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_finite](../c-runtime-library/reference/finite-finitef.md)|Averiguar si el valor de punto flotante de precisión doble dado es finito|[\<caps:sentence id\="tgt72" sentenceid\="8d081c50adeda3dde4cebab81a0b3583" class\="tgtSentence"\>System::Double::IsInfinity\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double.isinfinity.aspx)|  
|[floor, floorf](../c-runtime-library/reference/floor-floorf-floorl.md)|Hallar el entero más grande igual o menor que el argumento|[\<caps:sentence id\="tgt75" sentenceid\="609db9ab0433b647d5350d3b965d70f9" class\="tgtSentence"\>System::Math::Floor\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.floor.aspx)|  
|[fmod, fmodf](../c-runtime-library/reference/fmod-fmodf.md)|Hallar el resto del punto flotante|[\<caps:sentence id\="tgt78" sentenceid\="127a04426267ccb17fb4b566ad56de9c" class\="tgtSentence"\>System::Math::IEEERemainder\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)|  
|[\_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|Devolver la palabra de estado que contiene información sobre la clase de punto flotante|[System::Double::IsInfinity](https://msdn.microsoft.com/en-us/library/system.double.isinfinity.aspx), [System::Double::IsNegativeInfinity](https://msdn.microsoft.com/en-us/library/system.double.isnegativeinfinity.aspx), [System::Double::IsPositiveInfinity](https://msdn.microsoft.com/en-us/library/system.double.ispositiveinfinity.aspx), [System::Double::IsNan](https://msdn.microsoft.com/en-us/library/system.double.isnan.aspx)|  
|[\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md)|Invocar un controlador de interceptaciones definido por el usuario para las excepciones de punto flotante del IEEE|No es aplicable.|  
|[\_fpreset](../c-runtime-library/reference/fpreset.md)|Reinicializar el paquete matemático de punto flotante||  
|[frexp](../c-runtime-library/reference/frexp.md)|Calcular el valor exponencial|No es aplicable.|  
|[\_gcvt](../c-runtime-library/reference/gcvt.md), [\_gcvt\_s](../c-runtime-library/reference/gcvt-s.md)|Convertir el valor de punto flotante en una cadena de caracteres|[\<caps:sentence id\="tgt92" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[hypot, hypotf, hypotl, \_hypot, \_hypotf, \_hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|Calcular la hipotenusa de un triángulo rectángulo|No es aplicable.|  
|[\_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|Buscar elementos NaN \(que no son números\) en el valor de punto flotante de precisión doble dado|[\<caps:sentence id\="tgt97" sentenceid\="18f7dc07d0c506c23f2f7eb89262d274" class\="tgtSentence"\>System::Double::IsNan\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double.isnan.aspx)|  
|[labs](../misc/labs-llabs.md)|Devolver el valor absoluto de `long`|[\<caps:sentence id\="tgt100" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[ldexp](../c-runtime-library/reference/ldexp.md)|Calcular el producto del argumento y 2<sup>exp</sup> \(potencia especificada\)|[\<caps:sentence id\="tgt103" sentenceid\="839e85fe5fb98e8520d40a703d06932b" class\="tgtSentence"\>System::Math::Pow\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)|  
|[ldiv](../c-runtime-library/reference/ldiv-lldiv.md)|Dividir un entero `long` entre otro, de lo cual se obtiene un cociente y un resto|No es aplicable.|  
|[log, logf, log10, log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)|Calcular el logaritmo natural o de base 10.|[System::Math::Log](https://msdn.microsoft.com/en-us/library/system.math.log.aspx), [System::Math::Log10](https://msdn.microsoft.com/en-us/library/system.math.log10.aspx)|  
|[\_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|Extraer el valor exponencial del argumento de punto flotante de precisión doble|No es aplicable.|  
|[\_lrotl, \_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|Desplazar `unsigned long int` a la izquierda \(`_lrotl`\) o a la derecha \(`_lrotr`\)|No es aplicable.|  
|[\_matherr](../c-runtime-library/reference/matherr.md)|Tratar errores matemáticos|No es aplicable.|  
|[\_\_max](../c-runtime-library/reference/max.md)|Devolver el valor más alto de dos valores|[\<caps:sentence id\="tgt121" sentenceid\="6f9dcb228534c3e5b0013615b2b1d003" class\="tgtSentence"\>System::Math::Max\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.max.aspx)|  
|[\_\_min](../c-runtime-library/reference/min.md)|Devolver el valor más bajo de dos valores|[\<caps:sentence id\="tgt124" sentenceid\="ff471983fc666dec7ba58b17a0bf76e6" class\="tgtSentence"\>System::Math::Min\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.min.aspx)|  
|[modf, modff](../c-runtime-library/reference/modf-modff-modfl.md)|Dividir el argumento en entero y fracción|No es aplicable.|  
|[nan, nanf, nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|Devolver un valor NaN reservado|[\<caps:sentence id\="tgt129" sentenceid\="c251043405ffa73fe857c83428b58fdc" class\="tgtSentence"\>System::Double::NaN\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double.nan.aspx)|  
|[\_nextafter](../c-runtime-library/reference/nextafter-functions.md)|Devolver el siguiente elemento cercano representable|No es aplicable.|  
|[pow, powf](../c-runtime-library/reference/pow-powf-powl.md)|Calcular el valor elevado a una potencia|[\<caps:sentence id\="tgt135" sentenceid\="839e85fe5fb98e8520d40a703d06932b" class\="tgtSentence"\>System::Math::Pow\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)|  
|[printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [printf\_s, \_printf\_s\_l, wprintf\_s, \_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|Escribir datos en `stdout` según el formato especificado|[System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx), [System::Console::WriteLine](https://msdn.microsoft.com/en-us/library/system.console.writeline.aspx)|  
|[rand](../c-runtime-library/reference/rand.md), [rand\_s](../c-runtime-library/reference/rand-s.md)|Obtener el número seudoaleatorio|[\<caps:sentence id\="tgt141" sentenceid\="00574fde17be9de3e07567ef5abe0110" class\="tgtSentence"\>System::Random Class\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.random.aspx)|  
|[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|Redondear al entero más cercano en el formato de punto flotante|[\<caps:sentence id\="tgt143" sentenceid\="1c04aeb4aeff1752cb65adabcee29f53" class\="tgtSentence"\>System::Math::Round\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.round.aspx)|  
|[\_rotl, \_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|Desplazar `unsigned int` a la izquierda \(`_rotl`\) o a la derecha \(`_rotr`\)|No es aplicable.|  
|[\_scalb](../c-runtime-library/reference/scalb.md)|Escalar el argumento por una potencia de 2|No es aplicable.|  
|[scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|Multiplicar por la potencia integral de `FLT_RADIX`|No es aplicable.|  
|[scanf, wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|Leer datos de `stdin` según el formato especificado y escribir datos en la ubicación especificada|[System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx), [System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)|  
|[\_set\_controlfp](../c-runtime-library/reference/set-controlfp.md)|Establecer un nuevo valor de palabra de control|No es aplicable.|  
|[sin, sinf, sinh, sinhf](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|Calcular el seno y seno hiperbólico|[System::Math::Sin](https://msdn.microsoft.com/en-us/library/system.math.sin.aspx), [System::Math::Sinh](https://msdn.microsoft.com/en-us/library/system.math.sinh.aspx)|  
|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Hallar la raíz cuadrada|[\<caps:sentence id\="tgt162" sentenceid\="1a91af0bd8c63b4be64c7a0bec8dc8c4" class\="tgtSentence"\>System::Math::Sqrt\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.sqrt.aspx)|  
|[srand](../c-runtime-library/reference/srand.md)|Inicializar series seudoaleatorias|[\<caps:sentence id\="tgt165" sentenceid\="00574fde17be9de3e07567ef5abe0110" class\="tgtSentence"\>System::Random Class\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.random.aspx)|  
|[\_status87, \_statusfp, \_statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|Obtener la palabra de estado de punto flotante|No es aplicable.|  
|[strtod, \_strtod\_l, wcstod, \_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Convertir la cadena de caracteres en un valor de precisión doble|[\<caps:sentence id\="tgt169" sentenceid\="363f8f2cb09f8ca850491a65df66522e" class\="tgtSentence"\>System::Convert::ToDouble\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[tan, tanf, tanh, tanhf](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|Calcular la tangente y la tangente hiperbólica|[System::Math::Tan](https://msdn.microsoft.com/en-us/library/system.math.tan.aspx), [System::Math::Tanh](https://msdn.microsoft.com/en-us/library/system.math.tanh.aspx)|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)