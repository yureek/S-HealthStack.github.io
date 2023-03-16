---
title: healthstack.kit.task.activity.predefined
permalink: /kit/healthstack.kit.task.activity.predefined/index.html

---
//[kit](../../index.html)/[healthstack.kit.task.activity.predefined](index.html)



# Package healthstack.kit.task.activity.predefined



## Types


| Name | Summary |
|---|---|
| [TappingSpeedActivityTask](-tapping-speed-activity-task/index.html) | [androidJvm]<br>class [TappingSpeedActivityTask](-tapping-speed-activity-task/index.html)(val id: [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html), val taskId: [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html), val name: [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html), val description: [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html), val steps: [List](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/index.html)&lt;[Step](../healthstack.kit.task.base/-step/index.html)&lt;out [StepModel](../healthstack.kit.task.base/-step-model/index.html), *&gt;&gt; = listOf(         TappingSpeedIntroStep(             id, name,             TappingSpeedIntroModel(                 id, name             )         ),         TappingSpeedMeasureStep(             id, name,             TappingSpeedMeasureModel(                 id, name, null, measureTimeSecond = 20             )         ),         TappingSpeedIntroStep(             id, name,             TappingSpeedIntroModel(                 id, name, null, false             )         ),         TappingSpeedMeasureStep(             id, name,             TappingSpeedMeasureModel(                 id, name, null, false, 20             )         ),         TappingSpeedResultStep(             id, name,             TappingSpeedResultModel(                 id, name, null             )         )     ), isCompleted: [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) = false, isActive: [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) = true) : [ActivityTask](../healthstack.kit.task.activity/-activity-task/index.html) |

