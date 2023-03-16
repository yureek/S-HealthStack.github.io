---
title: TappingSpeedActivityTask
---
//[kit](../../../index.html)/[healthstack.kit.task.activity.predefined](../index.html)/[TappingSpeedActivityTask](index.html)/[TappingSpeedActivityTask](-tapping-speed-activity-task.html)



# TappingSpeedActivityTask



[androidJvm]\
fun [TappingSpeedActivityTask](-tapping-speed-activity-task.html)(id: [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html), taskId: [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html), name: [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html), description: [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html), steps: [List](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/index.html)&lt;[Step](../../healthstack.kit.task.base/-step/index.html)&lt;out [StepModel](../../healthstack.kit.task.base/-step-model/index.html), *&gt;&gt; = listOf(
        TappingSpeedIntroStep(
            id, name,
            TappingSpeedIntroModel(
                id, name
            )
        ),
        TappingSpeedMeasureStep(
            id, name,
            TappingSpeedMeasureModel(
                id, name, null, measureTimeSecond = 20
            )
        ),
        TappingSpeedIntroStep(
            id, name,
            TappingSpeedIntroModel(
                id, name, null, false
            )
        ),
        TappingSpeedMeasureStep(
            id, name,
            TappingSpeedMeasureModel(
                id, name, null, false, 20
            )
        ),
        TappingSpeedResultStep(
            id, name,
            TappingSpeedResultModel(
                id, name, null
            )
        )
    ), isCompleted: [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) = false, isActive: [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) = true)




