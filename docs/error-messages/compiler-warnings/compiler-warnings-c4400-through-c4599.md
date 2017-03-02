---
title: C4400 de advertencias del compilador mediante C4599 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4458
- C4459
- C4463
- C4464
- C4471
- C4472
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
dev_langs:
- C++
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 4ac033535632e94a365aa8dafd849f2ab28a3af7
ms.openlocfilehash: f6991adb0413221ddb101d07af41f83d1bbcabe2
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warnings-c4400-through-c4599"></a>C4400 de advertencias del compilador a través de C4599
Los artículos de esta parte de la documentación contienen información sobre un subconjunto de las advertencias del compilador de Visual C++. Puede tener acceso a información aquí o bien, en la **salida** ventana en Visual Studio, puede seleccionar un número de advertencia y, a continuación, elija la tecla F1.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Advertencia|Mensaje|  
|-------------|-------------|  
|[Compilador advertencia (nivel 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma 'nombre de macro': esperaba una cadena vacía no es válida|  
|[Compilador advertencia (nivel 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'tipo': no se admiten los calificadores const/volatile en este tipo|  
|[Compilador advertencia (nivel 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'campo': miembro es el campo de bits|  
|[Compilador advertencia (nivel 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|debe utilizar un operador PTR|  
|[Compilador advertencia (nivel 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|operador PTR no válido|  
|[Compilador advertencia (nivel 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|se ha omitido un punto en la directiva|  
|[Compilador advertencia (nivel 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'identificador': identificador es una palabra reservada|  
|[Compilador advertencia (nivel 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|se ha omitido el operando de la directiva|  
|[La advertencia C4407 compilador advertencia (nivel 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|al convertir entre distintas representaciones de puntero a miembro, el compilador puede generar código incorrecto|  
|[Compilador advertencia (nivel 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|anónimo ' struct | unión ' no declara ningún miembro de datos|  
|[Compilador advertencia (nivel 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|tamaño de instrucción máquina no válido|  
|[Compilador advertencia (nivel 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|tamaño no válido para el operando|  
|[Compilador advertencia (nivel 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'identificador': símbolo se resuelve como un registro de desplazamiento|  
|[Compilador advertencia (nivel 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'función': firma de la función contiene el tipo 'tipo'; Objetos de C++ son seguro pasar entre código puro y mixto o nativo.|  
|C4413 de advertencia del compilador|'classname::member': miembro de referencia se inicializa en un archivo temporal que no se conserva cuando termina el constructor|  
|[Compilador advertencia (nivel 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'función': salto short a la función ha convertido en near|  
|Advertencia del compilador (nivel 1) C4415|__declspec(code_seg('%$I')) duplicado|  
|Advertencia del compilador (nivel 1) C4416|__declspec(code_seg(...)) contiene una cadena vacía: omitido|  
|Advertencia del compilador (nivel 1) C4417|una creación de instancias de plantillas explícitas no puede omitir __declspec(code_seg(...)):|  
|Advertencia del compilador (nivel 1) C4418|__declspec(code_seg(...)) se ha omitido en una enumeración|  
|Advertencia del compilador (nivel 3) C4419|'%$I' no tiene ningún efecto cuando se aplica a una clase ref privada '%$S'.|  
|[Compilador advertencia (nivel 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'checked_operator': operador no disponible, se usa 'operador' en su lugar; comprobación en tiempo de ejecución puede estar en peligro|  
|Advertencia del compilador (nivel 3) C4421|'%$I': un parámetro de referencia en una función reanudable es potencialmente inseguro|  
|Advertencia del compilador (nivel 3) C4423|'std::bad_alloc': lo detectará la clase ('%$T') en la línea %d|  
|Advertencia del compilador (nivel 3) C4424|elemento catch para '%$T' precedido de '%$T' en la línea %d; puede tener como resultado un comportamiento impredecible si se produce 'std::bad_alloc'|  
|Advertencia del compilador (nivel 1) C4425|Una anotación SAL no se puede aplicar a '...'|  
|C4426 de advertencia del compilador|las marcas de optimización cambiadas después de incluir el encabezado, se puede deber a #pragma optimize()|  
|Advertencia del compilador (nivel 1) C4427|'%$L': desbordamiento en la división de constantes, comportamiento no definido|  
|[Compilador advertencia (nivel 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|nombre de carácter universal posiblemente incompleto o incorrectamente formado|  
|[Advertencia del compilador C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|falta el especificador de tipo; se presupone int. Nota: C++ no admite default-int|  
|[Compilador advertencia (nivel 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|falta el especificador de tipo; se presupone int. Nota: C no admite default-int|  
|[Advertencia C4434 de compilador advertencia (nivel 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|un destructor estático debe tener accesibilidad privada; se cambiará a acceso privado|  
|[Compilador advertencia (nivel 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'derived_class': diseño de objeto vd2 cambiará debido a la base virtual 'base_class'|  
|[Compilador advertencia (nivel 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|podría producirse un error de dynamic_cast de base virtual 'base_class' a 'derived_class' en el constructor o destructor con el objeto parcialmente construido|  
|[Compilador advertencia (nivel 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|podría producirse un error de dynamic_cast de base virtual 'base_class' a 'derived_class' en algunos contextos|  
|C4438 de advertencia del compilador|'%$S': no se puede llamar de forma segura / await: modo clrcompat. Si llama a '%$S' en CLR pueden causar daños principal de CLR|  
|[C4439 de advertencia del compilador](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'función': definición de función con un tipo administrado en la firma debe tener una convención de llamada __clrcall|  
|[Compilador advertencia (nivel 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|llamar a la nueva definición de convención de 'convención_de_llamada1' a 'calling_convenction2' se omite|  
|[Compilador advertencia (nivel 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|convención de llamada de 'convención_de_llamada1' se omite; 'calling_convention2' utilizado en su lugar|  
|Advertencia del compilador (nivel 1) C4442|terminador nulo incrustado en el argumento __annotation.  Se truncará el valor.|  
|Advertencia del compilador (nivel 1) C4443|se esperaba que el parámetro pragma fuera '0', '1' o '2'|  
|Advertencia del compilador (nivel 3) C4444|'identificador': el nivel superior '__unaligned' no está implementado en este contexto|  
|[Compilador advertencia (nivel 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'función': en un ' WinRT | administrado ' tipo de un método virtual no puede ser privado|  
|Advertencia del compilador (nivel 1) C4446|'%$S': no se puede asignar el miembro ' % $I ' en este tipo, debido a conflictos con el nombre de tipo. El método ha cambiado a ' % $I '|  
|Advertencia del compilador (nivel 1) C4447|firma 'main' sin el modelo de subprocesos. Considere el uso de ' int main (Array\<Platform:: String ^ > ^ args)'.|  
|C4448 de advertencia del compilador|'%$S' no tiene una interfaz predeterminada que se especifica en los metadatos. Preparación: '%$S', que puede producir un error en tiempo de ejecución.|  
|C4449 de advertencia del compilador|Un tipo no sellado debe marcarse como '[WebHostHidden]' ' %$S'|  
|C4450 de advertencia del compilador|'%$S' debe marcarse como '[WebHostHidden]' porque deriva de '%$S'|  
|Advertencia del compilador (nivel 4) C4451|'classname1::member': uso de la clase ref 'classname2::member' en este contexto, puede que no válido el cálculo de referencias de objeto en todos los contextos|  
|Advertencia del compilador (nivel 1) C4452|'identificador': no puede ser un tipo público en el ámbito global. Debe estar en un espacio de nombres es un elemento secundario en el nombre del archivo de .winmd de salida.|  
|Advertencia del compilador (nivel 1) C4453|'%$S': no se recomienda en la superficie publicada de un tipo público que no es un tipo de '[WebHostHidden]' '[WebHostHidden]'|  
|Advertencia del compilador (nivel 1) C4454|'%$S' está sobrecargado por algo más que el número de parámetros de entrada sin necesidad de [DefaultOverload] especificado. '%$D' de selección como sobrecarga predeterminada|  
|Advertencia del compilador (nivel 1) C4455|'operator %$I': los identificadores de sufijos literales que no comienzan por un carácter de subrayado están reservados|  
|Advertencia del compilador (nivel 3) C4456|declaración de 'identificador' oculta la declaración local anterior|  
|Advertencia del compilador (nivel 3) C4457|declaración de 'identificador' oculta el parámetro de función|  
|Advertencia del compilador (nivel 3) C4458|declaración de 'identificador' oculta el miembro de clase|  
|Advertencia del compilador (nivel 3) C4459|declaración de 'identificador' oculta la declaración global|  
|[Compilador advertencia (nivel 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|' WinRT | administrado ' operador 'operador' tiene un parámetro pasado por referencia. ' WinRT | administrado ' operador 'operador' tiene una semántica diferente del operador de C++ 'cpp_operator', ¿realmente pensaba en pasar por valor?|  
|[Error C4461 de compilador advertencia (nivel 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'classname': esta clase tiene un finalizador '! finalizador ' pero no un destructor ' ~ destructor '|  
|[Compilador advertencia (nivel 1) C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'tipo': no se puede determinar el GUID del tipo. El programa puede dar un error en tiempo de ejecución.|  
|C4463 de advertencia del compilador|desbordamiento; asignar 'value' para el campo de bits que sólo puede contener valores de 'mi_valuen' a 'max_value'|  
|C4464 de advertencia del compilador|ruta de acceso de inclusión relativas contiene '..'|  
|[Compilador advertencia (nivel 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|pragmas de control de punto flotante omitidas en /clr|  
|Advertencia del compilador (nivel 4) C4471|'enumeración': una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente (se presupone int)|  
|Advertencia del compilador (nivel 1) C4472|'identificador' es una enumeración nativa: agregue un especificador de acceso (pública y privada) para declarar un ' WinRT | administrada ' enum|  
|Advertencia C4480 de advertencia del compilador|extensión no estándar utilizada: especificar el tipo subyacente de la enumeración 'enumeración'|  
|[Compilador advertencia (nivel 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|ha utilizado una extensión no estándar: de reemplazo 'palabra clave'|  
|C4482 de advertencia del compilador|ha utilizado una extensión no estándar: enumeración 'enumeración' utilizada en el nombre completo|  
|Advertencia del compilador (nivel 1) C4483|error de sintaxis: se esperaba una palabra clave de C++|  
|[Advertencia C4484 de advertencia del compilador](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'función_de_reemplazo': coincide con el método de clase ref base 'función_de_clase_base', pero no está marcado como 'virtual', 'new' o 'override'; se supone 'new' (y no 'virtual')|  
|[C4485 de advertencia del compilador](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'función_de_reemplazo': coincide con el método de clase ref base 'función_de_clase_base', pero no está marcada 'new' u 'override'; se supone 'new' (y 'virtual')|  
|[Compilador advertencia (nivel 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'función': un método virtual privado de una clase ref o clase value se debe marcar como 'sealed'|  
|[Compilador advertencia (nivel 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'función_de_clase_derivada': coincide con el método no virtual heredado 'función_de_clase_base' pero no está explícitamente marcado como 'new'|  
|[Advertencia de compilador (nivel 1) de la advertencia C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'función': requiere la palabra clave 'palabra clave' para implementar el método de interfaz 'método_de_interfaz'|  
|[Compilador advertencia (nivel 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'especificador': no se permite en el método de interfaz 'método'; invalidar especificadores sólo se permiten en métodos de clase de valor y de clase ref|  
|[Compilador advertencia (nivel 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|'reemplazo': uso incorrecto del especificador de reemplazo; 'función' no coincide con un método de clase ref base|  
|Advertencia del compilador (nivel 1) C4491|'%s': tiene un formato de versión IDL no válido|  
|Advertencia del compilador (nivel 1) C4492|'%$S': coincide con el método de clase ref base '%$S', pero no está marcado como 'override'|  
|Advertencia del compilador (nivel 3) C4493|expresión de eliminación no tiene ningún efecto porque el destructor de 'tipo' no tiene accesibilidad 'public'|  
|Advertencia del compilador (nivel 1) C4494|'%$S' : se omite __declspec(allocator) porque el tipo de función devuelto no es un puntero o una referencia|  
|[Compilador advertencia (nivel 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|La 'especificación de vinculación' requiere el uso de la palabra clave 'extern' y debe preceder al resto de los especificadores|  
|[Advertencia de compilador (nivel 1) de la advertencia C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'identificador': superada, la longitud del nombre representativo nombre se ha truncado|  
|[Compilador advertencia (nivel 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'función': se ha quitado la función local no referenciada|  
|[Compilador advertencia (nivel 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|ninguna definición para la función inline 'función'|  
|[Compilador advertencia (nivel 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'función': función debe devolver un valor; 'void' tipo de valor devuelto supone|  
|C4509 de advertencia del compilador|ha utilizado una extensión no estándar: 'función' utiliza SEH y 'objeto' tiene un destructor|  
|[Compilador advertencia (nivel 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'clase': constructor predeterminado se define implícitamente como eliminada|  
|[Compilador advertencia (nivel 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'clase': constructor de copias se define implícitamente como eliminada|  
|[Compilador (nivel 4) de la advertencia C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'clase': el operador de asignación se define implícitamente como eliminada|  
|[Compilador C4513 de advertencia (nivel 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'clase': destructor se define implícitamente como eliminada|  
|[Compilador advertencia (nivel 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'función': se ha quitado la función inline a la que no se hace referencia|  
|[Compilador advertencia (nivel 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'namespace': espacio de nombres se utiliza a sí mismo|  
|[Compilador advertencia (nivel 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|'clase:: símbolo': las declaraciones de acceso están obsoletas; declaraciones using de miembros son una mejor alternativa|  
|[Compilador advertencia (nivel 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|las declaraciones de acceso están desusadas; las declaraciones using de miembros son una alternativa mejor|  
|[Compilador advertencia (nivel 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'especificador': clase de almacenamiento o especificadores inesperado de tipo aquí; pasa por alto|  
|Advertencia C4519 del compilador|los argumentos de plantilla predeterminados solo se permiten en una plantilla de clase|  
|[Compilador advertencia (nivel 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'clase': han especificado múltiples constructores de copia|  
|[Compilador advertencia (nivel 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'clase': especificado varios operadores de asignaciones|  
|[Compilador advertencia (nivel 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'clase': han especificado varios destructores|  
|[Advertencia de compilador advertencia (nivel 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'función': función miembro estática no puede reemplazar la función virtual 'función virtual' \n se omite el reemplazo, se ocultará la función virtual|  
|[Compilador advertencia (nivel 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|Controlador de excepciones de C++ utiliza, pero la semántica de desenredo no está habilitada. Especifique/EHsc|  
|Advertencia del compilador (nivel 1) C4531|Control de excepciones de C++ no está disponible en Windows CE. Utilice el control estructurado de excepciones|  
|[Advertencia de compilador (nivel 1) de la advertencia C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|'continue': saltar desde el bloque '__finally' tiene un comportamiento indefinido durante el control de finalización|  
|[Compilador advertencia (nivel 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|la inicialización de 'variable' se omite mediante 'etiqueta goto'|  
|[Compilador advertencia (nivel 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|'constructor' no será un constructor predeterminado para ' clase | struct' 'identificador' debido al argumento predeterminado|  
|[Compilador advertencia (nivel 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|llamar a _set_se_translator() requiere /EHa|  
|[Compilador advertencia (nivel 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'nombredetipo': nombre de tipo supera el límite de metadatos de 'character_limit' caracteres|  
|[Compilador advertencia (nivel 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'object': '.' aplicado al tipo no UDT|  
|[Compilador advertencia (nivel 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'tipo': no se admiten los calificadores const/volatile en este tipo|  
|[Compilador advertencia (nivel 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|dynamic_cast se ha utilizado para convertir a base inaccesible o ambigua; se producirá un error de prueba de tiempo de ejecución ('tipo1' a 'tipo2')|  
|[Compilador advertencia (nivel 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|'identificador' utilizado en el tipo polimórfico 'tipo' con/GR; puede producirse un comportamiento inesperado|  
|Advertencia del compilador (nivel 1) C4542|Se pasa por alto la generación de archivo de texto insertado combinado; no se puede escribir %$M en el archivo: '%s': %$e|  
|[Compilador advertencia (nivel 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|Texto insertado suprimido por el atributo 'no_injected_text'|  
|[Compilador advertencia (nivel 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'declaración': argumento de plantilla se omite en esta declaración de plantilla predeterminado|  
|[Compilador advertencia (nivel 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|la expresión antes de la coma se evalúa como una función a la que le falta una lista de argumentos|  
|[Compilador advertencia (nivel 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|falta la lista de argumentos de la llamada de función antes de la coma|  
|[Compilador advertencia (nivel 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'operador': un operador antes de una coma no tiene ningún efecto; se esperaba un operador con efectos secundarios|  
|[Compilador advertencia (nivel 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|la expresión antes de la coma no tiene ningún efecto; se esperaba una expresión con efectos secundarios|  
|[Compilador advertencia (nivel 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'operador': un operador antes de una coma no tiene ningún efecto; ¿realmente pensaba en 'operador'?|  
|[Compilador advertencia (nivel 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|la expresión se evalúa como una función a la que le falta una lista de argumentos|  
|[Compilador advertencia (nivel 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|la llamada a la función no tiene lista de argumentos|  
|[Compilador advertencia (nivel 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'operador': operador no tiene ningún efecto; se esperaba un operador con efectos secundarios|  
|[Compilador advertencia (nivel 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'operador': operador no tiene ningún efecto; ¿realmente pensaba en ' operador?|  
|[Compilador advertencia (nivel 3) C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'operador': Compruebe la prioridad de operador para posibles errores; Utilice paréntesis para aclarar la prioridad|  
|[Compilador advertencia (nivel 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|la expresión no tiene efecto; se esperaba una expresión con efecto secundario|  
|[Compilador advertencia (nivel 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|valor del argumento inmediato intrínseco 'valor' está fuera del intervalo ' lower_bound - upper_bound'|  
|[Compilador advertencia (nivel 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|'__assume' contiene el efecto 'efecto'|  
|[Compilador advertencia (nivel 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|valor del operando 'valor' está fuera del intervalo ' lower_bound - upper_bound'|  
|[Compilador advertencia (nivel 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'función': redefinición; la función gains|  
|[Compilador advertencia (nivel 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|'__fastcall' es incompatible con el ' / clr' opción: convertir a '\__stdcall'|  
|Advertencia del compilador (nivel 4) C4562|se requieren funciones con definición completa de prototipo al utilizar la opción '/clr': realizando la conversión de '()' a '(void)'|  
|[Compilador advertencia (nivel 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|el método 'método' de 'clase' 'classname' define el parámetro predeterminado no admitido 'parámetro'|  
|[Compilador advertencia (nivel 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'función': redefinición; el símbolo se declaró previamente con __declspec (modificador)|  
|[Compilador advertencia (nivel 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|carácter representado por el nombre de carácter universal 'char' no se puede representar en la página de códigos actual (%d)|  
|Advertencia del compilador (nivel 1) C4568|'%$S': ningún miembro coincide con la signatura de la invalidación explícita|  
|Advertencia del compilador (nivel 3) C4569|'%$S': ningún miembro coincide con la signatura de la invalidación explícita|  
|[Compilador advertencia (nivel 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'tipo': no se declara explícitamente como abstracto pero tiene funciones abstractas|  
|[Compilador C4571 de advertencia (nivel 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|Información: la semántica de catch(...) cambió desde Visual C++ 7.1; ya no se detectan excepciones estructuradas (SEH)|  
|[Compilador advertencia (nivel 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|El atributo [ParamArray] está obsoleto en/CLR, use '...' en su lugar|  
|Advertencia del compilador (nivel 1) C4573|el uso de '%$S' requiere que el compilador capture 'this', pero el modo de captura predeterminado actual no lo permite|  
|Advertencia del compilador (nivel 4) C4574|'Identificador' se define como '0': ¿pretendía usar '#if identificador'?|  
|Advertencia del compilador (nivel 1) C4575|'__vectorcall' es incompatible con el ' / clr' opción: convertir a '\__stdcall'|  
|[Compilador advertencia (nivel 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] está en desuso; especifique en su lugar System::Attribute o Platform::Metadata como clase base|  
|[Compilador advertencia (nivel 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|comportamiento en desuso: '"string" ' reemplazado por 'string' para procesar el atributo|  
|Advertencia del compilador (nivel 4) C4582|'%$S': no se llama al constructor implícitamente|  
|Advertencia del compilador (nivel 4) C4583|'%$S': no se llama al destructor implícitamente|  
|[Compilador C4584 de advertencia (nivel 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'clase1': clase base 'clase2' ya es una clase base de 'Clase3% '|  
|Advertencia del compilador (nivel 1) C4585|'clase': clase no sellada un WinRT 'clase ref pública' o bien debe ser sealed o derive de una existente|  
|Advertencia del compilador (nivel 1) C4586|'%$S': un tipo público no se puede declarar en un espacio de nombres de nivel superior llamado 'Windows'|  
|Advertencia del compilador (nivel 1) C4587|'anonymous_structure': cambio de comportamiento: constructor implícitamente ya no se llama|  
|Advertencia del compilador (nivel 1) C4588|'anonymous_structure': cambio de comportamiento: destructor implícitamente ya no se llama|  
|Advertencia del compilador (nivel 1) C4591|límite de profundidad de la llamada de 'constexpr' de %d superados (/ constexpr:depth\<número >)|  
|Advertencia del compilador (nivel 3) C4592|'función': 'constexpr' llamar a la evaluación; función que se llamará en tiempo de ejecución|  
|Advertencia del compilador (nivel 1) C4593|'función': límite de paso de evaluación de llamada de 'constexpr' de 'superado el límite de '; Utilice /constexpr:steps\<número > para aumentar el límite|  
|Advertencia del compilador (nivel 3) C4594|'%$S': el destructor no se llamará implícitamente si se inicia una excepción|  
|Advertencia del compilador (nivel 1) C4595|'%$S': cambio de comportamiento: el destructor no se llamará implícitamente si se inicia una excepción|
