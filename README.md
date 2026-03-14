# Scary-baboon-mod
Mods in 2026 version 826using UnityEngine;

public class GoldSystem : MonoBehaviour
{
    public int gold = 999999; // starting gold for testing
    public bool debugInfiniteGold = true;

    public void SpendGold(int amount)
    {
        if (debugInfiniteGold)
            return; // gold never decreases

        gold -= amount;
    }
}
