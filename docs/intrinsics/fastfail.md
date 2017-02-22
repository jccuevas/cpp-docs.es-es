---
title: "__fastfail | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# __fastfail
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Finaliza inmediatamente el proceso de llamada con un mínimo de sobrecarga.  
  
## Sintaxis  
  
```  
void __fastfail(unsigned int code);  
```  
  
#### Parámetros  
 \[in\] `code`  
 Una constante simbólica `FAST_FAIL_<description>` de winnt.h o wdm.h que indica el motivo de la terminación del proceso.  
  
## Valor devuelto  
 No se devuelve el intrínseco `__fastfail`.  
  
## Comentarios  
 El intrínseco `__fastfail` proporciona un mecanismo para una solicitud de *error rápido*, que es una manera de que se produzca un proceso posiblemente dañado para solicitar la terminación inmediata del proceso.  El recurso de control de excepciones normales no puede controlar los errores críticos que pueden haber dañado el estado del programa y que se acumulan sin posibilidad de recuperación.  Use `__fastfail` para terminar el proceso con una sobrecarga mínima.  
  
 Internamente, `__fastfail` se implementa mediante el uso de varios mecanismos específicos de la arquitectura:  
  
|Arquitectura|Instrucción|Ubicación del argumento de código|  
|------------------|-----------------|---------------------------------------|  
|x86|int 0x29|ecx|  
|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|int 0x29|rcx|  
|ARM|Código de operación 0xDEFB|r0|  
  
 Una solicitud de error rápido es independiente y normalmente solo requiere dos instrucciones para ejecutarse.  Una vez que se ha ejecutado una solicitud de error rápido, el kernel toma las medidas oportunas.  En el código en modo de usuario no hay ninguna dependencia de memoria, aparte del puntero de la instrucción cuando se provoca un evento de error rápido.  Esto maximiza la fiabilidad, incluso si hay daños graves en la memoria.  
  
 El argumento `code` \(una de las constantes simbólicas `FAST_FAIL_<description>` de winnt.h or wdm.h\) describe el tipo de condición de error y se incorpora en los informes de error de una manera específica del entorno.  
  
 Las solicitudes de error rápido en modo de usuario aparecen como una segunda excepción no continuable con el código de excepción 0xC0000409 y por lo menos con un parámetro de excepción.  El primer parámetro de excepción es el valor `code`.  Este código de excepción indica al Informe de errores de Windows \(WER\) y a la infraestructura de depuración que el proceso está dañado y que se deben realizar acciones mínimas en el proceso en respuesta al error.  Las solicitudes de error rápido en modo kernel se implementan mediante un código dedicado de comprobación de errores, `KERNEL_SECURITY_CHECK_FAILURE` \(0x139\).  En ambos casos, no se invocan controladores de excepciones, ya que se espera que el programa esté en un estado dañado.  Si hay presente un depurador, se le ofrece la oportunidad de examinar el estado del programa antes de la finalización.  
  
 La compatibilidad con el mecanismo de error rápido nativo comenzó en Windows 8.  Los sistemas operativos de Windows que no son compatibles con la instrucción de error rápido de forma nativa normalmente tratarán una solicitud de error rápido como una infracción de acceso, o como una comprobación de errores `UNEXPECTED_KERNEL_MODE_TRAP`.  En estos casos, el programa también se cierra, pero no necesariamente de una forma tan rápida.  
  
 `__fastfail` solo está disponible como intrínseco.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`__fastfail`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)], ARM|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)