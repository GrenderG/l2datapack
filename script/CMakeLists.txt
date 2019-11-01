cmake_minimum_required(VERSION 3.5)

add_subdirectory(AgitData)
add_subdirectory(AIScripts)
add_subdirectory(AreaData)
add_subdirectory(BuilderAliases)
add_subdirectory(CategoryData)
add_subdirectory(DoorData)
add_subdirectory(FString)
add_subdirectory(ItemData)
add_subdirectory(Manual)
add_subdirectory(MultiSell)
add_subdirectory(NpcData)
add_subdirectory(NpcPos)
add_subdirectory(PcParameters)
add_subdirectory(PetData)
add_subdirectory(Quests)
add_subdirectory(Recipes)
add_subdirectory(Setting)
add_subdirectory(SkillAcquire)
add_subdirectory(SkillData)
add_subdirectory(VehicleData)
add_subdirectory(WatchList)

add_custom_target(${PROJECT_NAME}-1-basics
    DEPENDS AgitData AreaData BuilderAliases CategoryData DoorData FString Manual MultiSell PcParameters PetData Recipes Setting VehicleData Quests WatchList
)

# Order is right to left <---o
add_custom_target(${PROJECT_NAME}-2-complex
    DEPENDS NpcPos NpcData SkillAcquire SkillData ItemData
)

add_custom_target(${PROJECT_NAME}-3-ai
    DEPENDS AIScripts
)

add_custom_target(${PROJECT_NAME}-0-all
    DEPENDS ${PROJECT_NAME}-3-ai ${PROJECT_NAME}-2-complex ${PROJECT_NAME}-1-basics
)
