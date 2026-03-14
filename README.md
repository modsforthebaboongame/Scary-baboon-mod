# Scary-baboon-mod
Mods in 2026 version 826
using UnityEngine;

public class PlayerHealth : MonoBehaviour
{
    public int health = 100;
    public bool godMode = true;

    public void TakeDamage(int damage)
    {
        if (godMode) return; // ignore damage

        health -= damage;

        if (health <= 0)
        {
            Die();
        }
    }

    void Die()
    {
        Debug.Log("Player died");
    }
}
