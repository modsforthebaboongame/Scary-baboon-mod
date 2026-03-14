# Scary-baboon-mod
Mods in 2026 version 826using UnityEngine;

public class DebugModSystem : MonoBehaviour
{
    [Header("Arms")]
    public Transform leftArm;
    public Transform rightArm;
    public float armLength = 2.5f;
    public bool longArmsEnabled = false;

    [Header("Health")]
    public int health = 100;
    public bool godMode = false;

    [Header("Gold")]
    public int gold = 999999;

    [Header("Staff Items")]
    public GameObject[] items;
    public Transform spawnPoint;
    int currentItem = 0;

    void Update()
    {
        // Toggle Long Arms
        if (Input.GetKeyDown(KeyCode.Alpha1))
        {
            longArmsEnabled = !longArmsEnabled;
            SetArmLength();
        }

        // Toggle God Mode
        if (Input.GetKeyDown(KeyCode.Alpha2))
        {
            godMode = !godMode;
        }

        // Cycle Staff Item
        if (Input.GetKeyDown(KeyCode.E))
        {
            currentItem++;
            if (currentItem >= items.Length)
                currentItem = 0;
        }

        // Spawn Item From Staff
        if (Input.GetMouseButtonDown(0))
        {
            Instantiate(items[currentItem], spawnPoint.position, spawnPoint.rotation);
        }

        // Debug Gold
        if (Input.GetKeyDown(KeyCode.G))
        {
            gold += 1000;
            Debug.Log("Gold: " + gold);
        }
    }

    void SetArmLength()
    {
        if (leftArm != null && rightArm != null)
        {
            float scale = longArmsEnabled ? armLength : 1f;
            leftArm.localScale = new Vector3(1, scale, 1);
            rightArm.localScale = new Vector3(1, scale, 1);
        }
    }

    public void TakeDamage(int damage)
    {
        if (godMode) return;

        health -= damage;

        if (health <= 0)
        {
            Debug.Log("Player died");
        }
    }

